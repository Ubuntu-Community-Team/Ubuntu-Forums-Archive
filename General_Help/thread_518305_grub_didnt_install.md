---
title: "grub didnt install"
date: 2007-08-05
forum: General Help
---

### Post by jbseven on 2007-08-05
Hello all,

Im new to the linux os and decided to start with ubuntu 7.04 but ran into some trouble while installing. Please bear with me while i try to provide the relevant information:
Im running a windows xp system on a k8nf4g motherboard and the following disk setup(in windows and bios)
c: -  65GB primary partition on disk 1 - winxp os and ntfs)
d: -  80GB single partition on disk2 ntfs)
e: -  40GB single partition on disk3 (for linux install)
f: - 250GB single partition on disk4 ntfs
g:- 400GB logical partition on disk1 ntfs

i booted the live cd and installed it to disk3 without any issues. setup finished, asked me to remove the cd and reboot but now it just boots into windows xp.

i read the forum's tutorial on grub and tried the following at the livecd terminal window:
sudo grub
find /boot/grub/stage1 ->returns (hd1,0)
root (hd1,0)
setup (hd0)
quit.

it said the operation was successful but i still boot straight into windows like b4. any ideas on how i can fix this?
all help appreciated
-jb

---

### Post by Bachstelze on 2007-08-05
Try [this method](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows#head-bf3232f10ddf1b078de064622ccbb25225cdb3c0) for installing GRUB.

---

### Post by jbseven on 2007-08-05
that almost seemed to work. 
i used the grub bootloader cd instructions u posted from the link 
and managed to get grub working. 
only problem is now ubuntu doesnt start. 'unable to mount' errors for all 3 options (recovery,memtest)
windows xp loads as normal.
any suggestions?
thanks again
-jb

---

