---
title: "Ubuntu/Vista Dual Boot Problem"
date: 2007-06-18
forum: General Help
---

### Post by ashz on 2007-06-18
Personally I hate Windoze but my friend still insists upon it!!

Either way I burnt off a copy of Ubuntu 7.04 for him, so he could get it setup for dual boot on his machine at home.

Anyways he rings me up today, and explains that he has installed it but when it boots up, it boots up into Vista and does not give him a choice of OS's.

Anyone got any ideas, im sure that Ubuntu is loaded on there, it's just not coming up as a boot option.

I would put this down to grub, but how I get it to recongise both OS's on a dual boot machine I dont know!!

Thanks in advance.

Ash

---

### Post by ashz on 2007-06-18
Bump!

---

### Post by confused57 on 2007-06-18
I'm hesitant to give any specific advice, since I'm not sure how well the Ubuntu install succeeded for him.

What I would suggest is to download & burn a copy of the Super Grub Disk:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

If SGD boots his Linux with no problems, then it would probably be safe to install grub to the mbr.

In fact, Linux can be added to the Vista bootloader:
[http://neosmart.net/wiki/display/EBCD/Linux](http://neosmart.net/wiki/display/EBCD/Linux)

grub would need to be installed to the Ubuntu root partition, using the live cd to do this:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by ashz on 2007-06-18
Thanks for the advice, im not sure how well it worked either!!

I think im going to have to go round at have a look,

thanks again
ash

---

