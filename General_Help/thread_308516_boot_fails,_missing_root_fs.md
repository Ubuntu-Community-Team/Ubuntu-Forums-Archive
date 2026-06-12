---
title: "boot fails, missing root fs"
date: 2006-11-28
forum: General Help
---

### Post by romeozor on 2006-11-28
greetingz,

i wanted to install ubuntu on my Asus A6Ja (a.k.a. S96J). the livecd stared up without any problems, i walked the path of the installer, and at the partition i edited it maually. i got 3 partitions, 1st (sda1) is windows, 2nd (sda2) is root, and 3rd (sda3) is linux-swap.
so the installer starts and ends without any problems, but after reboot, ubuntu wont start up, it stucks at Mounting root filesystem; Waiting for root filesystem, and drops me in a shell saying:
ALERT /dev/sda2 does not exist. Dropping to a shell!

so i dont really understand, did i do something wrong? is my hardware unsupported, or i just need to do some magic to make it work?

btw gentoo worked without any problems

---

### Post by TwoWordz on 2006-11-28
if you boot a live CD, what is the output of fdisk -l?

TW

---

