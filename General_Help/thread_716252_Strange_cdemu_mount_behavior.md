---
title: "Strange cdemu mount behavior"
date: 2008-03-05
forum: General Help
---

### Post by cszikszoy on 2008-03-05
Hello,

I've been messing with cdemu for quite a while trying to get this Nautilus Actions script work for mounting images.  At some point yesterday it was working fine, then after a reboot, no luck.

I've been debugging the script (code below)
```
#!/bin/bash
# (C) 2006 AMSOFT - Version 6.10.28-5.00
# Mount CD images
# Get filename extension and make it lower-case
EXT=`echo $1 | sed -e 's/.*\.//'`
EXT_LOW=`echo $EXT | tr 'A-Z' 'a-z'`
# Main
if [ $EXT_LOW == "cue" -o $EXT_LOW == "iso" -o $EXT_LOW == "mds" -o $EXT_LOW == "ccd" -o $EXT_LOW == "nrg" ]; then
  # Find a free DEV to mount
  DEV=$((`cdemu -b system status | cut -f 6 -d " " | grep 0 -n -m 1 | cut -c 1`-3))
  if [ $DEV -lt "0" ]; then
    zenity --error --text "You can not mount any more images."; exit 1
  fi
  # Only allow mounting an image once
  FILE="`basename \"$1\"`"
  MOUNTED="`cdemu -b system status | grep \"$FILE\" | cut -f 17 -d " "`"
  if [ "$MOUNTED" != "" ]; then
    IMAGEMOUNTED="`basename $MOUNTED`"
    DEVMOUNTED="`cdemu -b system status | grep \"$FILE\" | cut -f1 -d " " | sed -e 's@:@@'`"
echo $DEVMOUNTED" "$IMAGEMOUNTED" "$MOUNTED" "$FILE" "$1
    if [ "$IMAGEMOUNTED" = "$FILE" ]; then
      zenity --info --text "'${FILE}' is already mounted on 'cdemu$DEVMOUNTED'."; exit 1
    fi
  fi
  # DEV needs to be between 0 and 2
  if [ $DEV -ge "0" -a $DEV -le 2 ]; then
echo $DEV
    cdemu -b system load $DEV $1 &&
    mount /media/cdemu$DEV # && gnome-open "/media/cdemu${DEV}"
    # Uncomment (by removing '#' from) last part of previous line to open mounted cd in new window
  fi
  # If directory is empty, then release cdemu
  if ! [ "$(ls -A /media/cdemu${DEV})" ]; then
    cdemu -b system unload $DEV
  fi
else
  zenity --info --text "'${FILE}' is not a CD image."; exit 1
fi
```The output when I explicitly open the script by:
```
chris@chris-laptop:/home/chris/Desktop$ /bin/Image-mount /home/chris/Desktop/file.iso
mount: no medium found

```The image does not get mounted.

However, when I execute the line above the mount command myself in the terminal by:
"cdemu -b system load 0 "/home/chris/Desktop/file.iso" "

it will mount fine, except that it shows up in /media/cdemu1, instead of /media/cdemu0.
```
chris@chris-laptop:/media/cdemu0$ ls
chris@chris-laptop:/media/cdemu0$ cd /media/cdemu1
chris@chris-laptop:/media/cdemu1$ ls
Installer  macromedia dreamweaver.sfv  readme.nfo  Update

```CDemu's status *thinks* that the device is still in device 0, but it gets mounted to /dev/cdemu1?```
chris@chris-laptop:/media/cdemu0$ cdemu -b system status
Devices status:
DEV   LOADED     TYPE       FILENAME
0     1          PARSER-ISO /home/chris/Desktop/MacromediaDreamweaver8.iso
1     0          N/A        N/A
2     0          N/A        N/A

```Does this make any sense?  Any ideas?

Thanks,
-Chris

---

