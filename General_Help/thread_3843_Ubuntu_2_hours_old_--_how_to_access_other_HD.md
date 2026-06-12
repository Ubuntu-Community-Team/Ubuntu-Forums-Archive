---
title: "Ubuntu 2 hours old -- how to access other HD"
date: 2004-11-09
forum: General Help
---

### Post by littlegreenman on 2004-11-09
Hi guys...

Newbie here... Linux newbie as well... have very basic knowledge of it.

How do I mount my 2 Windows HD? It was preety straightforward in Debian. Don't know how to do it with ubuntu.

Can someone help. the /mount command doesn't seem to do it for me... or maybe I don't know how :-) 

These are the HD I have on /dev
hda
hda1
hdb
hdb1
hdb2
hdb5
hdc

I have 2 HD, 1 fully windows, the other half linux half windows

hdb1 seems to be the one where ubuntu is installed
it says mount: according to mtab, /dev/hdb1 is already mounted on /

but when I try for instance mount hda or mount hda1 it says
mount: can't find /dev/hda1 in /etc/fstab or /etc/mtab

my /etc/fstab has the following:
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdb1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdb5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

my /etc/mtab has the following:
dev/hdb1 / ext3 rw,errors=remount-ro 0 0
proc /proc proc rw 0 0
sysfs /sys sysfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
tmpfs /dev/shm tmpfs rw 0 0
usbfs /proc/bus/usb usbfs rw 0 0


any ideas, help, whatever?

thanks
littlegreenman

---

### Post by flow on 2004-11-09
here is what i use.. see whether it works for you
just change hda1 to hd** and change the filesystem as well
rw is read write
ro is read only

/dev/hda1	/media/driveC	vfat	rw,umask=0,user,codepage=850,exec 0 0
/dev/hda5	/media/driveD	ntfs	nls=iso8859-1,ro,umask=0 0 0

---

### Post by wazoo42 on 2004-11-09
Just make sure to make the folders before (/media/driveC/ and /media/driveD) you try to mount to them.

---

