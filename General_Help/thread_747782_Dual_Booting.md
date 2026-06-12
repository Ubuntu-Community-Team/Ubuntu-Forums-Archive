---
title: "Dual Booting"
date: 2008-04-06
forum: General Help
---

### Post by larryi5 on 2008-04-06
Im currently running ubuntu 7.10 and i was wondering about dual booting. Actully the only reason im using it right now is cuz i messed up a partition the otherday with xp and installed it over xp. I was wondering if anyone knows any good guides for dual booting 7.10 with xp, osx, and other versions of linux. Everythings already messed up if i make more mistakes it wont hurt lol.

---

### Post by chewearn on 2008-04-06
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)
[https://help.ubuntu.com/community/MacBook](https://help.ubuntu.com/community/MacBook)

---

### Post by sekinto on 2008-04-06
1) Back up your data in case anything goes wrong.

2) Resize your partition taking up all the space so that you allocate enough space for the OS you will be dual booting Ubuntu with (you can do this with gParted from a Ubuntu live CD).

3) Make a new partition in the empty space
Windows: NTFS
Pre-NT Windows: FAT32
OS X: HFS+ (I think that is right)
Linux: XFS, JFS, ReseirFS, Ext4, Ext3, Ext2, et cetera...

4) Install your new OS on the partition.

5) If the OS asks to write over the MBR say NO. If it does it automatically you will have to rewrite GRUB to the MBR, you can do this from a terminal on your Ubuntu live CD:
1 - sudo grub
2 - root (hd0,0) - replace (hd0,0) with your Ubuntu partition, if it is on the second partition of your first hard drive you would use (hd0,1), for the fourth partition on your second hard drive you would do (hd1,3), et cetera...
3 - setup (hd0) - replace (hd0) with the partition Ubuntu is on, if it is the third partition you would use (hd2), for the first you would use (hd0), et cetera...
4 - exit

6) Now you have to edit your /boot/grub/grub.conf or /boot/grub/menu.list file, you want to add a boot option, and what you type there will depend on what OS you are dual booting. For example, if booting another Linux OS you can do it the same way as Ubuntu, just changing the location of / (root) and the kernel, for Windows however you would need to use chainloader.
Here are instructions of how to boot certain OSs using Grub:
[With Linux, see figure 4-10]("http://tldp.org/HOWTO/Remote-Serial-Console-HOWTO/configure-boot-loader-grub.html") 
[With Windows]("http://www.linuxquestions.org/questions/linux-newbie-8/booting-windows-from-grub-577176/")

---

