---
title: "how to mount USB stick in recovery mode"
date: 2014-07-29
forum: General Help
---

### Post by raymondvillain on 2014-07-29
Trying to salvage files on a hard drive on which 14.04 failed to install.

I can boot to the hard drive but only in recovery mode.  At the command prompt, I can navigate around and find the documents, photos, etc. that I want to save.

I've loaded a 64 Gb USB stick.

Is it possible to mount the USB stick from the command line?  Then I could use the cp command and save myself from ignominy.

Any and all suggestions greatly appreciated.

---

### Post by raymondvillain on 2014-07-29
Think I've figured it out.  First unmount the file system and remount so it can be made read-write:

mount -o remount,rw /   (This is discussed here: [http://askubuntu.com/questions/117950/hoew-do-i-change-file-system-in-recovery-mode-to-read-write-mode](http://askubuntu.com/questions/117950/hoew-do-i-change-file-system-in-recovery-mode-to-read-write-mode) )

Then find out the location of the USB stick:

 fdisk -l

Then make a mount point:

mkdir /media/usb

and mount the usb drive:

 mount /dev/sdd1 /media/usb

and copy:

cp -r /home /media/usb

All this is explained very well in [http://askubuntu.com/questions/37767/how-to-access-a-usb-flash-drive-from-the-terminal-how-can-i-mount-a-flash-driv](http://askubuntu.com/questions/37767/how-to-access-a-usb-flash-drive-from-the-terminal-how-can-i-mount-a-flash-driv)

---

