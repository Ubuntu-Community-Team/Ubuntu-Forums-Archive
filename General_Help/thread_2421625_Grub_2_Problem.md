---
title: "Grub 2 Problem"
date: 2019-06-24
forum: General Help
---

### Post by freddy58 on 2019-06-24
I have Desktop Computer, and I have Linux Mint 19.1 Tessa Cinnamon on one Hard Drive.  On anther Hard Drive, I have Windows 7 Pro installed.  A couple days ago I installed Ubuntu on the same Hard Drive Linux Mint is mounted on.  When Installing Ubuntu, I choose to install beside Linux Mint.  I can Get On Linux Mint, go to GParted and go look at the disk Linux Mint is Installed, I can see the 2 partitions, and see both Partitions contain Data

Now the Problem I am having, when I start my Computer and it goes through the Bios then the Grub 2 screen, Ubuntu is not listed there.  How would tell Grub 2 to put Ubuntu on the Grub2 Start up screen?

---

### Post by oldfred on 2019-06-24
Are all systems in same boot mode, or all UEFI or all BIOS?
How you boot install media is then how it installs.

       Shows installer with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI) 
    
If all are in same boot mode, then run this:
sudo update-grub

If that does not work do this:
 May be best to see details, use ppa version with your live installer (2nd option) or any working install,  not older Boot-Repair ISO:
Please copy & paste link to the Boot-info summary report ( do not post report), the auto fix sometimes can create more issues.
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) & 
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

