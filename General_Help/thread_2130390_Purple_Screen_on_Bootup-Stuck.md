---
title: "Purple Screen on Bootup-Stuck"
date: 2013-03-29
forum: General Help
---

### Post by jimb0b360 on 2013-03-29
I'm stuck on a purple screen on boot at the moment. I've tried booting into recovery mode using shift to get into GNU GRUB v2.00 , going into advanced options for Ubuntu and hitting Ubuntu, with Linux 3.5.0-17-generic (recovery mode), but this brings up a Busybox v1.19.3 ash built in shell, which I haven't a clue what to do with. It also gives a ton of error messages going into recovery mode, like:
5.607159 lost page write due to I/O error on loop0
5.607286 loop: write error at byte offset 15627979776 length 1024
mounting /sys on /root/sys failed: No such file or directory.
There are lots more with decimal numbers at the beginning, and I'm a newb so I only understand that it can't access something to write something... Or something...
I installed using the windows install tool onto my secondary partition, allocating 20gb/250 ish gb of space last night, was on it for a while setting up python, apache and applying a gedit theme and some addons. Then I shut down and went to bed. I have tried to boot into the Ubuntu with generic Linux mode that doesn't have recovery mode, but that also gets stuck at Loading Initial Ramdisk.
there seems to be a lot of errors here and I don't understand why. Laptop is a 64-bit Celeron T3500 with built in graphics. Model is Samsung S3510.
Im confused.
Jim

EDIT: Laptop boots into win7 fine, just tested. I believe I can access the partition from windows as well.

---

### Post by wildmanne39 on 2013-03-29
Hi, please try what this link suggests, please read carefully.
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
Thanks

---

### Post by jimb0b360 on 2013-03-29
> **Wild Man said:**
> Hi, please try what this link suggests, please read carefully.
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
Thanks
I am unsure how this applies to my problem. I will repeat: I can't boot into my Ubuntu at all, it worked the first time but now it won't. I can boot into windows, but trying Ubuntu it freezes at a purple screen. Recovery mode also won't work. Please read O/P carefully. I attempted nomodeset, but it is stuck, once again, on a purple screen. The instructions for ACPI could be much clearer, as it doesn't list where the command is to be entered - Grub? Busybox? Terminal (which I can't access as my Linux wont work!)?

EDIT: Turns out I'm slightly dumb and you insert the ACPI into the same edit box as nomodeset after it, but it still doesn't work. Only slightly stupid.

---

### Post by wildmanne39 on 2013-03-29
Those parameters will most likely allow you to boot  ubuntu.

---

### Post by jimb0b360 on 2013-03-29
None of them do. I've now tried every one of them, on their own, with another, all together, every combination possible. No luck. I've just re-installed Ubuntu and I'm hoping that when I reboot the laptop I can get in.

---

