---
title: "Making Ubuntu the Default Boot Partition"
date: 2007-07-13
forum: General Help
---

### Post by Orann on 2007-07-13
I've recently just built myself a computer and as soon as It got working, I Installed Ubuntu on it (My first time with Linux). I've been having some wireless network troubles with it (see my thread in the Wireless and Networking forums), so I decided to try out Mandriva while I was looking for a solution. In doing this, I partitioned my HardDrive so that Ubuntu and Mandriva both had their own partition, and so that I didn't have to wipe out Ubuntu to do this.

Both are great operating systems, And I'd like to keep playing around with both. My problem begins here, currently my system automatically boots up into Mandriva, and I need it to boot into Ubuntu so I can fix some of the Wireless problems I was having there (Thanks to some help from KevDog).

Could anyone tell me how to change what Partition I boot into when I turn on my computer?

Thanks.


P.S: Just something I should add, I've seen a lot of talk about GRUB etc. on this matter, Am I missing something? What should I be looking for?

---

### Post by mikewhatever on 2007-07-13
GRUB boot loader should give you options in its menu to boot both. Don't you see [this screen]("http://users.bigpond.net.au/hermanzone/p15.htm") at boot? Try hitting Esq if there is if there is only the count down.

---

### Post by Wim Sturkenboom on 2007-07-13
Grub is a bootloader. A bootloader is the first program that is started after the PowerOn SelfTest. The other bootloader that is often used in Linux is Lilo.
I don't know which one Mandriva is using, so that's the first thing to find out. If you don't know, a way to find out might be pressing <esc> or <ctrl>X (control and X simultaneously) immidiately after the POST while your PC boots (but it might be a bit tricky to get the right moment).

It's not 100% clear to me if you get a menu during the boot where you can choose between Mandriva or Ubuntu; something tells me you don't get that.


If not, we need to know your partitions. Please post the output of *fdisk -l* and of *df* .
The first command gives all partitions and the second one gives the partitions of the current operating system. Your output will look similar to the one below.
```

root@btd-techweb01:~# **fdisk -l**

Disk /dev/hda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1024     8225248+  83  Linux
/dev/hda2            1025        1090      530145   82  Linux swap
/dev/hda3            1091        4278    25607610   83  Linux
/dev/hda4            4279        4865     4715077+   5  Extended
/dev/hda5            4279        4865     4715046   83  Linux
root@btd-techweb01:~# **df**
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/hda1              8224992   2278396   5946596  28% /
/dev/hda3             25606820     47864  25558956   1% /server
/dev/hda5              4714896   3077724   1637172  66% /home
root@btd-techweb01:~#

```
Also indicate which partitions are for Ubuntu and (if you can remember) if you creted a separate /home partition for Ubuntu.

I'm not a bootloader specialist, so somebody else might be able to help you further from there.


PS The fdisk command needs root privileges.

---

### Post by Saxomophone on 2007-07-13
I'm not sure if this will help, but reinstalling the grub files is an option. You can boot from the livecd and follow these instructions to do that... [http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD](http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD)

Not sure if that's your problem though.

---

