---
title: "why won't grub2 splash image apear at boot up"
date: 2017-03-04
forum: General Help
---

### Post by jeff666 on 2017-03-04
i followed steps here [https://help.ubuntu.com/community/Grub2/Displays](https://help.ubuntu.com/community/Grub2/Displays)

Can't get my splash images to appear Im testing with one from  grub2-splashimages. 

```

$cat /etc/default/grub

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT=""
GRUB_CMDLINE_LINUX=""
GRUB_BACKGROUND=/usr/share/images/grub/apollo.tga

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
uGRUB_INIT_TUNE="480 440 1"

```

i changed the name of the apollo.tga image for convince. I also edited /etc/grub.d/05_debian_theme ( [I]menu_color_highlight=white/black) this should make it tranparent

```
#!/bin/sh
set -e

# grub-mkconfig helper script.
# Copyright (C) 2010  Alexander Kurtz <kurtz.alex@googlemail.com>
#
# GRUB is free software: you can redistribute it and/or modify
# it under the terms of the GNU General Public License as published by
# the Free Software Foundation, either version 3 of the License, or
# (at your option) any later version.
#
# GRUB is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
# GNU General Public License for more details.
#
# You should have received a copy of the GNU General Public License
# along with GRUB.  If not, see <http://www.gnu.org/licenses/>.

# Include the GRUB helper library for grub-mkconfig.
. /usr/share/grub/grub-mkconfig_lib

# We want to work in /boot/grub/ only.
test -d /boot/grub; cd /boot/grub

# Set the location of a possibly necessary cache file for the background image.
# NOTE: This MUST BE A DOTFILE to avoid confusing it with user-defined images.
BACKGROUND_CACHE=".background_cache"

set_default_theme(){
    case $GRUB_DISTRIBUTOR in
        Tanglu|Ubuntu|Kubuntu)
            # Set a monochromatic theme for Tanglu/Ubuntu.
            echo "${1}set menu_color_normal=white/black"
            echo "${1}set menu_color_highlight=white/black"

            if [ -e /usr/share/plymouth/themes/default.grub ]; then
                sed "s/^/${1}/" /usr/share/plymouth/themes/default.grub
            fi
            # For plymouth backward compatiblity. Can be removed
            # after xenial.
            if [ -e /lib/plymouth/themes/default.grub ]; then
                sed "s/^/${1}/" /lib/plymouth/themes/default.grub
            fi
            ;;
        *)
            # Set the traditional Debian blue theme.
            echo "${1}set menu_color_normal=white/black"
            echo "${1}set menu_color_highlight=white/black"
            ;;
    esac
}

module_available(){
    local module
    for module in "${1}.mod" */"${1}.mod"; do
        if [ -f "${module}" ]; then
            return 0
        fi
    done
    return 1
}

set_background_image(){
    # Step #1: Search all available output modes ...
    local output
    for output in ${GRUB_TERMINAL_OUTPUT}; do
        if [ "x$output" = "xgfxterm" ]; then
            break
        fi
    done

    # ... and check if we are able to display a background image at all.
    if ! [ "x${output}" = "xgfxterm" ]; then
        return 1
    fi

    # Step #2: Check if the specified background image exists.
    if ! [ -f "${1}" ]; then
        return 2
    fi

    # Step #3: Search the correct GRUB module for our background image.
    local reader
    case "${1}" in
        *.jpg|*.JPG|*.jpeg|*.JPEG) reader="jpeg";;
        *.png|*.PNG) reader="png";;
        *.tga|*.TGA) reader="tga";;
        *) return 3;; # Unknown image type.
    esac

    # Step #4: Check if the necessary GRUB module is available.
    if ! module_available "${reader}"; then
        return 4
    fi

    # Step #5: Check if GRUB can read the background image directly.
    # If so, we can remove the cache file (if any). Otherwise the backgound
    # image needs to be cached under /boot/grub/.
    if is_path_readable_by_grub "${1}"; then
        rm --force "${BACKGROUND_CACHE}.jpeg" \
            "${BACKGROUND_CACHE}.png" "${BACKGROUND_CACHE}.tga"
    elif cp "${1}" "${BACKGROUND_CACHE}.${reader}"; then
        set -- "${BACKGROUND_CACHE}.${reader}" "${2}" "${3}"
    else
        return 5
    fi

    # Step #6: Prepare GRUB to read the background image.
    if ! prepare_grub_to_access_device "`${grub_probe} --target=device "${1}"`"; then
        return 6
    fi

    # Step #7: Everything went fine, print out a message to stderr ...
    echo "Found background image: ${1}" >&2

    # ... and write our configuration snippet to stdout. Use the colors
    # desktop-base specified. If we're using a user-defined background, use
    # the default colors since we've got no idea how the image looks like.
    # If loading the background image fails, use the default theme.
    echo "insmod ${reader}"
    echo "if background_image `make_system_path_relative_to_its_root "${1}"`; then"
    if [ -n "${2}" ]; then
        echo "  set color_normal=${2}"
    fi
    if [ -n "${3}" ]; then
        echo "  set color_highlight=${3}"
    fi
    if [ -z "${2}" ] && [ -z "${3}" ]; then
        echo "  true"
    fi
    echo "else"
    set_default_theme "  "
    echo "fi"
}

# Earlier versions of grub-pc copied the default background image to /boot/grub
# during postinst. Remove those obsolete images if they haven't been touched by
# the user. They are still available under /usr/share/images/desktop-base/ if
# desktop-base is installed.
while read checksum background; do
    if [ -f "${background}" ] && [ "x`sha1sum "${background}"`" = "x${checksum}  ${background}" ]; then
        echo "Removing old background image: ${background}" >&2
        rm "${background}"
    fi
done <<EOF
648ee65dd0c157a69b019a5372cbcfea4fc754a5  debian-blueish-wallpaper-640x480.png
0431e97a6c661084c59676c4baeeb8c2f602edb8  debian-blueish-wallpaper-640x480.png
968ecf6696c5638cfe80e8e70aba239526270864  debian-blueish-wallpaper-640x480.tga
11143e8c92a073401de0b0fd42d0c052af4ccd9b  moreblue-orbit-grub.png
d00d5e505ab63f2d53fa880bfac447e2d3bb197c  moreblue-orbit-grub.png
f5b12c1009ec0a3b029185f6b66cd0d7e5611019  moreblue-orbit-grub.png
EOF

# Include the configuration of desktop-base if available.
if [ -f "/usr/share/desktop-base/grub_background.sh" ]; then
    . "/usr/share/desktop-base/grub_background.sh"
fi

# First check whether the user has specified a background image explicitly.
# If so, try to use it. Don't try the other possibilities in that case
# (#608263).
if [ -n "${GRUB_BACKGROUND+x}" ]; then
    set_background_image "${GRUB_BACKGROUND}" || set_default_theme
    exit 0
fi

# Next search for pictures the user put into /boot/grub/ and use the first one.
for background in *.jpg *.JPG *.jpeg *.JPEG *.png *.PNG *.tga *.TGA; do
    if set_background_image "${background}"; then
        exit 0
    fi
done

# Next try to use the background image and colors specified by desktop-base.
if set_background_image "${WALLPAPER}" "${COLOR_NORMAL}" "${COLOR_HIGHLIGHT}"; then
    exit 0
fi

# If we haven't found a background image yet, use the default from desktop-base.
case $GRUB_DISTRIBUTOR in
    Ubuntu|Kubuntu)
        ;;
    Tanglu)
        if set_background_image "/usr/share/images/grub/grub.png"; then
            exit 0
        fi
        ;;
    *)
        if set_background_image "/usr/share/images/desktop-base/desktop-grub.png"; then
            exit 0
        fi
        ;;
esac

# Finally, if all of the above fails, use the default theme.
set_default_theme

```
[/I]
after running 'sudo update-grub'

```
Generating grub configuration file ...
Found background: /usr/share/images/grub/apollo.tga
Found background image: /usr/share/images/grub/apollo.tga
Found linux image: /boot/vmlinuz-4.4.0-64-generic
Found initrd image: /boot/initrd.img-4.4.0-64-generic
Found linux image: /boot/vmlinuz-4.4.0-62-generic
Found initrd image: /boot/initrd.img-4.4.0-62-generic
Found Windows Boot Manager on /dev/sda2@/EFI/Microsoft/Boot/bootmgfw.efi
Adding boot menu entry for EFI firmware configuration
done

```

i also ran to make sure that color change happend 

```
cat /boot/grub/grub.cfg | grep apollo
background_image -m stretch /usr/share/images/grub/apollo.tga
if background_image /usr/share/images/grub/apollo.tga; then
cat /boot/grub/grub.cfg | grep black
  set menu_color_normal=white/black
  set menu_color_highlight=white/black
  if [ -e ${prefix}/gfxblacklist.txt ]; then
    if hwmatch ${prefix}/gfxblacklist.txt 3; then

```

does this have to do with hardware it doesn't look like its getting much resolution until into the boot process im not currently using:
-gtx 1060 Nivida graphics card 
I am using :
-i7 6700k
-asus pro/gaming z170

---

### Post by jeff666 on 2017-03-04
so i edited 


```
# Set a monochromatic theme for Tanglu/Ubuntu.
            echo "${1}set menu_color_normal=white/black"
            echo "${1}set menu_color_highlight=white/black"

```

to: 
```


# Set a monochromatic theme for Tanglu/Ubuntu.
            echo "${1}set menu_color_normal=red/black"
            echo "${1}set menu_color_highlight=red/black


```

So the transparent 'black' should be working! it knows about the image just doesn't want to display it I'm going to try a different image for giggles!  If some one could give me directions on how to make a image for grub2 with ink scape i could try a image with like 3 colors see if that works!

ill also add: 

```

$ grub-install -V
grub-install (GRUB) 2.02~beta2-36ubuntu3.7

$ uname -r
4.4.0-64-generic

```

any help would be awesome thanks!

---

### Post by speartip on 2017-03-05
What version of Ubuntu are you using??
On 16.04 it's as simple as dropping an image into the /boot/grub folder & running "sudo update-grub".
Although I did change the image to a .tga image first using Gimp. Don't think that was necessary though.

---

### Post by jeff666 on 2017-03-06
same version 16.04 Ubuntu server

if you read some of the info i posted update-grub does recognize the image so grub should know about it that isn't a issue (although  i will give putting image in /boot/grub a try)

could you please explain to me how to make image .tga in gimp?



i also tried a different screen (older serial connector), i tried using my graphics card, those also didn't work. 

I  do think this is a hard wear issue however i did get it work in Debian  before (few months back) which is odd shouldn't both be the same grub:

grub-install (GRUB) 2.02~beta2-36ubuntu3.7


also one idea i had:

Is this related to secure boot I'm having trouble  also with installing drivers and virtual box? im not fully sure on how  efi, secure boot, etc work so a brief explanation would be golden. can i install grub to be efi and linux to not  be efi? (so windows will still work my bios csm mode will always boot  efi first over legacy)



this is really getting annoying  tried comment out background line in '/etc/default/grub' and put the image in /boot/grub ran update-grub (which saw the image) and then ran 'reboot' Nothing! still doesn't work im going to tinker with the bois boot setting see if that changes the result ill still post even though this isn't getting any attention.

---

### Post by deadflowr on 2017-03-06
Try this:
Open the image in gimp
Go to the section Image.
Then go to scale image.
Do not change the image size, but rather reset the interpolation from cubic to linear and click OK.
Now open File and go down to Export and this will save the image.
Save the image as a png image and change the save location to somewhere in your home folder.

Then cp the file into the /boot/grub folder and re-run the grub-update command.

See if that works

---

### Post by jeff666 on 2017-03-06
@deadflower thanks good for future reference making grub images

unfortunately i screwed up my boot-loader somehow so just did a fresh install with  csm legacy only mode and that solved pretty much every problem i was having with grub, virtual-box, graphics card driver, speakers, etc. So solved, i guess it was secure boot blocking some sort of ability to load drivers (which is a head ach to understand)

---

