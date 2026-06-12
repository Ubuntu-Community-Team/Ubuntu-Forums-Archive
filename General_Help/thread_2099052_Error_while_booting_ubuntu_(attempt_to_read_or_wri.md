---
title: "Error while booting ubuntu (attempt to read or write outside of disk 'hd0')"
date: 2012-12-28
forum: General Help
---

### Post by Jitesh G on 2012-12-28
ok guys,i just installed ubuntu 12.10 along side windows 7 and after installation i restarted pc and after selecting UBUNTU from GRUB it was showing me attempt to read or write outside of disk 'hd0'
Error: You need to load kernel first 
press any key to continue.....
 any one know how to fix this issue????

---

### Post by LinXNut on 2012-12-28
When you press any key does it just restart your computer? Or does it goto a command line?

---

### Post by Jitesh G on 2012-12-29
IT goes back to screen where i have to select OS to boot

---

### Post by oldfred on 2012-12-29
Post the link to the BootInfo report that this creates. Is part of Boot-Repair:

[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 
[http://sourceforge.net/p/boot-repair/home/Home/](http://sourceforge.net/p/boot-repair/home/Home/)
[https://help.ubuntu.com/community/UbuntuSecureRemix](https://help.ubuntu.com/community/UbuntuSecureRemix)

---

### Post by Jitesh G on 2012-12-30
now when i press any key to continue it shows up
 Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(0,0)

and i have also tried boot repair but nothing happened

---

### Post by oldfred on 2012-12-30
That may be because it did not install correctly or you did not have a "good"  ISO to use.

I might verify ISO with md5 sum.
       [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

