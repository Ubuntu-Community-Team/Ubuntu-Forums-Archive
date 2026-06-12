---
title: "Installed Ubuntu with USB, now I can't mount USB sticks"
date: 2008-06-05
forum: General Help
---

### Post by -::Bas::- on 2008-06-05
Ok, here's the problem:
I've managed to install my Ubuntu with a USB pen, instead of the usual cd-rom. I made a bootable usb-stick, with the desktop version of ubuntu (following these steps: [http://forums.msiwind.net/ubuntu/installing-ubuntu-the-wind-t226.html](http://forums.msiwind.net/ubuntu/installing-ubuntu-the-wind-t226.html) )

Now when i try to mount a usb pen, I just can't
This is my fstab file:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb5
UUID=93e5e904-6326-4473-bfd0-00c0e67ea8e9 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=57AFCAEBE30EE9E6 /media/sda5     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sdb1
UUID=E47C96327C95FF8A /media/sdb1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sdb7
UUID=73C44B3113E618A7 /media/sdb7     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sdb6
UUID=773efeb3-b8a2-4dc6-a61f-628cacc48a6f none            swap    sw              0       0
/dev/sdc1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
```

and I can see where my problem lies: my /dev/sdc1 , which is the usb-pen, seems to get mounted as cdrom, and it shouldn't.
How do I correct this prioblem, so that every time i insert a usb-pen i gets mounted as usb-pen instead of a cd-rom??

Help is greatly appreciated!

---

### Post by Kernel_Krunch on 2008-06-05
> **-::Bas::- said:**
> 

Help is greatly appreciated!

Do you need the data?  quickest way is umount it and delete the partitions with cfdisk /dev/sdc, then partition it back to ext3

---

### Post by -::Bas::- on 2008-06-05
Thanks for your answer, but the usb drive doesn't get mounted properly in the first place, so there's nothing to unmount.

This is the message that I get when sticking my usb pen in a slot:
```
Cannot mount volume.
Invalid mount option when attempting to mount the volume 'TOSHIBA'.
```

(i have a toshiba usb pen)

So every time I put is a usb pen, (i have four or five laying around the place), it gets mounted as a cdrom, since during the installation of ubuntu I installed it from my usb stick (damn that was fast!!), and that got mounted as a cdrom because the ubuntu installer is supposed to run from cdrom, otherwise all the references would not work.

I digress here, what it boils down to, that I need to change the default how usb drives get mounted, they should get mounted as usb-dongle or whatever.

/ok, googling my error code got me tons of hits, I will look at that in the morning and keep you posted (should've googled before nagging at you guys)

---

### Post by -::Bas::- on 2008-06-05
ok, that was easy, 

where I found 
```
/dev/sdc1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
```
in my fstab file, i changed it to
```
# /dev/sdc1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
```
(i.e. i placed a # at the beginning of the line so it's not used)

Courtesy of [https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

