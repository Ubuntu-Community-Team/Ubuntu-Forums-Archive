---
title: "dualboot win7 and 8, want to add ubuntu"
date: 2013-01-27
forum: General Help
---

### Post by youdoofus on 2013-01-27
I have a dualboot win7/8 system and want to add ubuntu to the mix. I think its about the same as having a single boot system and adding linux to it, but i dont wanna mess it up. Ive read some threads about how to do what im asking, but im not a compiler type of person. Can i just install from the iso disc i made without issue? Sorry for the newb type of question, but like i said, i just dont want a huge project to fix if i mess it up LoL

Thanks in advance for any/all help guys/gals!!!

---

### Post by oldfred on 2013-01-27
What is partition layout. If you have used all 4 primary partitions it will not be so easy. Or if you used Windows to create many partitions it will convert to dynamic which does not work with Linux.

If you have a spare primary or have already created an extended partition then you just have to make room for Ubuntu and let it install.

Note that Windows moves the boot files of a second install to the first install. So from grub2's boot menu you will only have one Windows boot entry and from Windows will be able to boot either version. 

Post this from liveCD/DVD/flash drive installer in live mode using terminal.
```

sudo fdisk -lu
```

---

### Post by youdoofus on 2013-01-27
right on. im currently at work, but ill get that info for ya when i get home in a few hours. I think im only at 3 partitions now tho :) thanks for the quick reply!! you guys are always VERY helpful!!!!

---

