---
title: "Dual OS"
date: 2013-06-08
forum: General Help
---

### Post by Muh Ridwan Idris on 2013-06-08
hello,

I want make dual OS in my laptop.
first, I installed windows 7, then I installed Linux 12.04 LTS, after that. I restart my laptop, but I can not choose the OS (windows or linux)
directly running to Linux,
Any body able to help me, how I can get dual OS. without reinstall

---

### Post by decrepit on 2013-06-08
Don't panic!!! unless you've chosen to overwrite windows should still be there. There is a setting in grub, where the choice of boot options is either hidden or is only there for a very brief time. Watch closely when it boots, you should get a screen that asks you to choose OS, all you have to do is hit any key to keep that screen displayed.
If you don't get it, open a terminal and type, 

sudo fdisk -l

enter your password when it asks for it.
Then it should show all the partitions on your computer, windows should be the one with NTFS file system.

---

### Post by zombifier25 on 2013-06-08
Try running this command in the terminal:
```
sudo update-grub
```
Also post the output. Unless you have chosen to eliminate Windows (which means you're screwed), it should be there, and Grub should be able to pick it up (don't know why it didn't the first time around)

---

### Post by Mark Phelps on 2013-06-08
When you installed Ubuntu, it overwrote the code in the MBR with GRUB, so now, it boots directly into Ubuntu.

The terminal code zombier25 gave you should fix that by adding and entry to the GRUB config file for the Windows 7 Loader.

After that, when you reboot, you should see a GRUB menu.

---

