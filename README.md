# Image previews using Überzug for Vifm (vi file manager)

![image](https://raw.githubusercontent.com/cirala/vifmimg/master/screenshot.png)

This script is used along Vifm for generating image previews for various file types in Vifm.

Video previews are also supported by using ffmpegthumbnailer and works very well but just
like the PDF previews there is a minor flash between each preview, this is due to
ffmpegthumbnailer generating the preview file.

GIF files are as of now in the works, it _works_ but in order to break out of the
animation loop the user needs to hit the CTRL-C. Sometimes this breaks the preview
entirely. When resizing the terminal window the animation replays.
There is room for improvement here.

PDF preview is also supported, this is done via pdftoppm and works almost flawlessly,
a minor flash between the previews occur due to pdftoppm generating the image.

## Installation
1. Copy the **vifmimg** and **vifmrun** scripts to a folder that is included in your $PATH
variable for easy access to the files.

2. Edit your **~/.config/vifm/vifmrc** file and add fileviewer properties like so:


```
    fileviewer *.pdf
        \ vifmimg pdfpreview %px %py %pw %ph %c
        \ %pc
        \ vifmimg clear

    fileviewer *.bmp,*.jpg,*.jpeg,*.png,*.xpm
        \ vifmimg draw %px %py %pw %ph %c
        \ %pc
        \ vifmimg clear

    fileviewer *.gif
        \ vifmimg gifpreview %px %py %pw %ph %c
        \ %pc
        \ vifmimg clear
```

3. In order to launch Vifm with image preview from now you'll need to use the supplied
**vifmrun** script

## Prerequisites
* Überzug and Vifm (isn't this obvious?)
* ffmpegthumbnailer
* ImageMagick
* pdftoppm

## Credits
* Seebye for creating [Überzug](https://github.com/seebye/ueberzug) and the initial script
that this script is heavily based upon.
* [Ranger's](https://github.com/ranger/ranger) approach to file previewing as an
inspiration source.
