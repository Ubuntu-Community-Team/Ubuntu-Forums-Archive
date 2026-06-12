---
title: "mounted fat32 partition not showing up on desktop"
date: 2007-01-08
forum: General Help
---

### Post by fokuslee on 2007-01-08
here is what i did 
in fstab
/dev/sda3       /media/sda3     vfat iocharset=utf8,umask=000   0        0
in media 
mkdir sda3
mount /dev/sda3 /media/sda3 
after even reboot sda3 does not show up on desktop 
 
so for now i did
ln -s /media/sda3 /home/fokuslee/Desktop/sda3

Is there away to make ubuntu auto detect the mount and creat a desktop shortcut for the partition? 
if that is not possible how do i change the symlink icon from a folder to the cool file-system icon?

SOLVED just needed a reboot lmao

---

### Post by goatflyer on 2007-01-08
I think you want this:

Alt-F2, run gconf-editor

goto Apps>Nautilus>Desktop

check the box labelled "Volumes Visible"

---

### Post by fokuslee on 2007-01-08
actually the volume visible is already checked (ticked) 
usb harddrive and thumbdrive all show up automatically
any other ideas? 
oh by the way i found an icon in /usr/share/icons/HUMAN/ to use 
just in case anyone else is interested.

---

