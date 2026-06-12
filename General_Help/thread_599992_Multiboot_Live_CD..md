---
title: "Multiboot Live CD."
date: 2007-11-01
forum: General Help
---

### Post by hodgestructure on 2007-11-01
recently, I play with vistape live cd.
After booting, I found the menu is very like 
grub4dos and menu.lst.

So I tried to copy the files in ubuntu.iso to vistape.iso,
and edited the menu.lst to the following


title Ubuntu
kernel /casper/vmlinuz boot=casper ramdisk_size=1048576 
root=/dev/cd

initrd /casper/initrd.gz

and this works, i.e I can press "Ubuntu" and boot into Ubuntu.


But it's somehow different from what I have seen by directly boot from 
original Ubuntu CD. I didn't see the original menu of Ubuntu CD,
I mean I can't see "Start or Install Ubuntu", 
"Start Ubuntu in safe graphics mode"...etc...


So I tried to edit the menu.lst to the following:

title ubuntu
chainloader --force /isolinux/isolinux.bin
boot

But it says that :

 ISOLINUX 3.36 Debian-2007-08-30 isolinux : Image checksum error, sorry

-------------------------

Please help me on this issue, if it's possible, thank you.
The following are the link of vistape project.

[http://www.vistape.net/](http://www.vistape.net/)

The following are the menu after booting into vistape

[http://rapidshare.com/files/66835912/vistape.bmp.html](http://rapidshare.com/files/66835912/vistape.bmp.html)

And  I want to get the following after press "ubuntu"

[http://rapidshare.com/files/66836439/ubuntu.bmp.html](http://rapidshare.com/files/66836439/ubuntu.bmp.html)

---

