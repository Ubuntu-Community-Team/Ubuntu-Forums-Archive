---
title: "External USB HD issue"
date: 2007-05-05
forum: General Help
---

### Post by mulanee on 2007-05-05
Hi there,

I use my xubuntu box (P3 500) as home server (http,samba).
No problem under 6.10.
With Feisty , I face to transfer issue between client (win2000) and my Xubuntu box:wide file freeze xubuntu and client threw samba.It occurs only with my external USB HD.
This is my fstab:
> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=92906ca5-2c7f-4506-ac18-5a978296c98e /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda3
UUID=6298bb48-be2b-413d-bcde-0c4cba2547f1 /home           ext3    defaults       0       2
# /dev/hda2
UUID=8479ab1b-8aa0-4b07-8844-811c8922363e none            swap    sw            0       0
# /dev/hdb1
UUID=7fe129d4-43f2-4bf6-8a23-a48383b95ce2 /home2          ext3    defaults      0       2
/dev/cdrom        /media/cdrom0   udf,iso9660 user,noauto                 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto              0       0
#/dev/sda1
UThis is my mtab:
> /dev/hda1 / ext3 rw,errors=remount-ro 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
/sys /sys sysfs rw,noexec,nosuid,nodev 0 0
varrun /var/run tmpfs rw,noexec,nosuid,nodev,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
procbususb /proc/bus/usb usbfs rw 0 0
udev /dev tmpfs rw,mode=0755 0 0
devshm /dev/shm tmpfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
/dev/hda3 /home ext3 rw 0 0
/dev/hdb1 /home2 ext3 rw 0 0
/dev/sda1 /LaCie vfat rw,noexec,nosuid,nodev,fmask=0111,dmask=0000,gid=100 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw 0 0
Here is my setup:
[http://ebgy.ath.cx/phpsysinfo/?template=blue]("http://ebgy.ath.cx/phpsysinfo/?template=blue")

--
Emmanuel

---

### Post by mulanee on 2007-05-06
More elements:
It's not a question of file size ; 
Some avi works some don't.
The same avi can be transferred in an internal HD and freezes the same station by trying to transfer in external USB HD

---

