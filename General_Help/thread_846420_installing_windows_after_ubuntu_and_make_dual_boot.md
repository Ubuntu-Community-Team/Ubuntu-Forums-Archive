---
title: "installing windows after ubuntu and make dual booting system"
date: 2008-07-01
forum: General Help
---

### Post by AnasZ on 2008-07-01
I have installed ubuntu to my laptop "TOSHIBA - TECRA" and removed completely windows OS was installed on it. 
now my hard drive is showing the following partions in partion editor GParted:
1.  /dev/sda1    ext3        size 54.45GiB
2.  /dev/sda2    extended    size  1.44GiB
3.  /dev/sda5    linux-swap  size  1.44GiB
now I want to make a dual booting system ubuntu and windows from my recovery CD. 
is this possible or not? please help me and give me step by step becuase i am still new in Linux system

thank you,

---

### Post by logos34 on 2008-07-01
If linux is taking up the whole drive, you'll need to shrink it down to make room for windows.  You'll also need to reinstall Grub because windows installation will overwrite the MBR with it's own bootloader

[http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm](http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm)

---

