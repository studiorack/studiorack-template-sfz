# studiorack-template-sfz
![Release](https://github.com/studiorack/studiorack-template-sfz/workflows/Release/badge.svg)

Audio plugin starter template using SFZ to build bundles using:

* sfzlint 0.1.x
* ffmpeg 4.4.x
* sfizz_render 1.1.x


## Installation

Install ffmpeg in order to covert .flac files to .ogg:

    https://www.ffmpeg.org/download.html


## Usage

Add your .flac sample files in:

    ./Samples

Then update the .sfz file with the sample paths:

    ./studiorack-template-sfz.sfz

Read more about the [SFZ format](https://sfzformat.com).


## Testing your plugin

Install the linter using:

    pip install git+git://github.com/kmturley/sfzlint.git

Then run using:

    sfzlint studiorack-template-sfz.sfz


## Build (manual)

Compress lossless version:

    zip -r ./studiorack-template-sfz.zip *

Create lossy version:

    for i in ./Samples/*.flac; do ffmpeg -i "$i" -b:a 128k "${i%.*}.ogg"; done
    sed -i 's/flac/ogg/g' 'studiorack-template-sfz.sfz'

Compress lossy version:

    zip -r ./studiorack-template-sfz-lossy.zip *


## Build (automatic)

Release a plugin version on GitHub by simply creating a version tag:

    git tag v0.0.1
    git push && git push origin --tags

This will run an automated build and release process on GitHub Actions:

    .github/workflows/release.yml


## Resources & guides

* [SFZ syntax](https://sfzformat.com)
* [SFZ tools](https://sfzformat.com/software/tools)
* [SFZ tutorials](https://sfzformat.com/tutorials/basics)


## Contact

For more information please contact kmturley
