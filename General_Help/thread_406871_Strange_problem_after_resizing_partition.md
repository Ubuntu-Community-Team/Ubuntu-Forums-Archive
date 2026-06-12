---
title: "Strange problem after resizing partition"
date: 2007-04-11
forum: General Help
---

### Post by panicbyte on 2007-04-11
OK, a few weeks ago I started running out of space in my linux partition, so I managed to shrink my windows (NTFS) partition (/dev/sda1/) and make my linux partition (/dev/sda2/) larger. However when i completed this task my linux partition went from being (/dev/sda2) to (/dev/sda3/) and this caused a problem with grub. however, I was able to use a bootable CD to change the grub boot menu config file to be /sda3/ however, i just did a kernel update and grub got changed back to /dev/sda2

is there a way that I can fix this problem and make /dev/sda3 become /dev/sda2?

OR

fix ubuntu so the next kernel update won't mess up grub?

---

### Post by indytim on 2007-04-11
Check out the following for tons of pertinent information on Grub related:

[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html]("http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html")

To avoid the Grub growth on kernel updates see the section where links are discussed.  I'm just encorporating it into my multi-boot environment.  Should be able to verify that it works with a presumed kernel update on Kubuntu 7.04 this weekend.

Good Luck,
IndyTim

---

