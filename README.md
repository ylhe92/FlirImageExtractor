# Flir Image Extractor CLI

The email address attached to this on PyPi may not be monitored, open issues on the [GitHub repo](https://github.com/nationaldronesau/FlirImageExtractor) to ensure a response

Feel free to submit any pull requests or issues, this is in active development. Also let me know if you are successful in using this on cameras not listed below.

FLIR® thermal cameras like the FLIR ONE® include both a thermal and a visual light camera.
The latter is used to enhance the thermal image using an edge detector. The resulting image is saved as a
jpg image but both the original visual image and the raw thermal sensor data are embedded in the jpg metadata.

This Python CLI that allows you to extract the original photo and thermal sensor values converted to temperatures, normalize the temperature range and output the photos to different color maps.

## Requirements and Install

This tool relies on `exiftool`. It should be available in most Linux distributions (e.g. as `perl-image-exiftool` in Arch Linux or `libimage-exiftool-perl` in Debian and Ubuntu). Links for downloading the Mac version and more information is available on the [ExifTool site](https://sno.phy.queensu.ca/~phil/exiftool/index.html).

To install exiftool on Windows for use in this CLI, download the `exiftool` windows executable from [here](https://exiftool.org/exiftool-11.93.zip). Extract `exiftool(-k).exe` and rename to `exiftool.exe`. Copy this executable to `C:\Windows` on your computer. You will need admin permissions to do this. Doing this will make `exiftool` avaiable to the CLI.

It also requires other python packages, *matplotlib*, *numpy* and *pillow*, which are installed when installed through pip.

```bash
sudo apt update
sudo apt install exiftool
```

You can install the CLI using pip
```bash
pip install flir-image-extractor-cli
```

## Usage

You can start the CLI using the terminal.
```bash
flir-image-extractor-cli
````


#### Resulting Plot and Saved Images
The CLI is able to output 3 folders of images with the `bwr`, `gnuplot`, and `gist_ncar` colormaps from matplotlib. You can define the pallete(s) that you would rather use.

## Supported/Tested Cameras

- Flir One (thermal + RGB)
- Xenmuse XTR (thermal + thumbnail, set the subject distance to 1 meter)
- AX8 (thermal + RGB)

Other cameras might need some small tweaks (the embedded raw data can be in multiple image formats). Let me know if you succesfully use other cameras so they can be added to this list.

## Development
Install the required packages using [Pipenv](https://pipenv.kennethreitz.org/en/latest/). Then run `pre-commit install` to install the pre-commit hooks. Note that this tool is intended to work on Windows as well as Unix operating systems so use os.path functions to manipulate file paths instead of string manipulation.
## Credits

This CLi was developed using this repo:
https://github.com/Nervengift/read_thermal.py
