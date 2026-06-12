---
title: "Grub problem..Error 22"
date: 2007-01-21
forum: General Help
---

### Post by warez86 on 2007-01-21
I am having problems with grub booting ubuntu.

Whenever I boot I am given the option of windows or ubuntu, windows works fine, but when I select ubuntu it comes up with error 22 partion not found. I have tried editing the root(hd3,2) line to where I think the correct partion is, but it does not work. The only way I can get ubunto to boot is to delete the root(hd3,2) line

***
menu.lst
***
title		Ubuntu, kernel 2.6.17-10-generic
root		(hd3,2)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/sdc3 ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root		(hd3,2)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/sdc3 ro single
initrd		/boot/initrd.img-2.6.17-10-generic
boot

title		Ubuntu, memtest86+
root		(hd3,2)
kernel		/boot/memtest86+.bin
quiet
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Home Edition
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1


**
device.map
**
(hd0)	/dev/hdc
(hd1)	/dev/sda
(hd2)	/dev/sdb
(hd3)	/dev/sdc


**
fstab
**
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdc3
UUID=0222f729-710f-4d4d-b60a-cee486ffa140 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hdc1
UUID=288C9F808C9F476A /media/hdc1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda1
UUID=00249C98249C91F0 /media/sda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sdb1
UUID=FCF42810F427CBA8 /media/sdb1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sdc1
UUID=0E10D3A810D39555 /media/sdc1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sdc2
UUID=8a86a3cd-130f-4c6d-9e60-31fff0b2c87b none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hda        /media/cdrom1   udf,iso9660 user,noauto     0       0

any help would be appreciated
thank you

---

### Post by louieb on 2007-01-21
Edit: Forget that. I just looked closer at your device map now I'm stumped too.

---

