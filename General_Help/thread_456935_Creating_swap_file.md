---
title: "Creating swap file"
date: 2007-05-28
forum: General Help
---

### Post by dolbinau on 2007-05-28
Hi,

Mistakenly I didn't setup a swap partition, is it possible for me to create a swap file (rather than swap partition) post the Ubuntu installation?

thanks 

If it is easy to create a partition, how would I go about that?

---

### Post by Lucifiel on 2007-05-28
Okay, you can try Parted Magic or GParted . Just create a partition called "linux-swap" and set it as double the size of your RAM. 

You might be able to create a swap partition using your Ubuntu LiveCd but I wouldn't count on it as the GParted version included with the LiveCd is very outdated. 

Parted Magic
[http://partedmagic.com/](http://partedmagic.com/)  

GParted
[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

---

### Post by astoltz on 2007-05-28
You cannot change a mounted partition.  So if you currently have only one partition that Ubuntu is installed and running from, you'll have to boot from the live CD before any changes can be made.  If you have "spare" partition, you can use Gparted to un-mount and chage the type and / or size to suit your swap needs.

---

### Post by Xbehave on 2007-05-28
you wont need twice your ram,
for most usage 512MB or 1GB is good (1g if you have enough hd)
if you can reparation its a risky process but easier than mounting a partion in a file

---

