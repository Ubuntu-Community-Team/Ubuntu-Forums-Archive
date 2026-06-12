---
title: "error when using grub"
date: 2017-06-07
forum: General Help
---

### Post by ahmad-nahali on 2017-06-07
when i did this command [HTML]sudo grub-install --target=i386-pc --boot-directory="/media/ahmad/WINDOWS/boot" /dev/sdb1[HTML]
then this happened 
[HTML]grub-install: warning: File system `fat' doesn't support embedding.
grub-install: warning: Embedding is not possible.  GRUB can only be installed in this setup by using blocklists.  However, blocklists are UNRELIABLE and their use is discouraged..
grub-install: error: will not proceed with blocklists.[/HTML]
Im trying to make a bootable windows usb

---

### Post by yancek on 2017-06-07
Your install command is wrong.  You need to install to the MBR of the device not the FAT32 partition which is what you are doing so make the one change at the end of the command from "/dev/sdb1" to " /dev/sdb" (without quotes).  It's always better to use windows software if you can.  The link below gives a very detailed explanation on creating a bootable windows usb installation system from Ubuntu.  I expect you will need to manually create the grub.cfg file which is also explained at the link below. 

[http://onetransistor.blogspot.ch/2014/09/make-bootable-windows-usb-from-ubuntu.html](http://onetransistor.blogspot.ch/2014/09/make-bootable-windows-usb-from-ubuntu.html)

---

