---
title: "GPARTED Error/Partition"
date: 2020-08-14
forum: General Help
---

### Post by ow9ner on 2020-08-14
Hey guys, I've just recently installed Ubuntu Linux (like just 5 hours ago), and I really want to create a new primary partition. I searched for it and came across GParted. now I installed GParted using the command terminal (Ctrl+Alt+T) and typing sudo apt-get install gparted. I resized my disk and the instruction told me to select 'primary partition'. However, when I clicked on Partition and on New, I am not able to select the Primary Partition option. It is stuck on Logical Partition. So I gladly searched on the web again for a solution. They told me to live boot from my usb. So, I did. But, it's all the same. I wanna use the primary partition that I've created for my Windows 10, as I'll be needing it (using Ubuntu is quite overwhelming, so if I can, I'd want to be able to switch to Windows freely). Please help me. I'm using Ubuntu 20.04 LTS.

---

### Post by oldfred on 2020-08-14
If you are using the now 35 year old BIOS/MBR configuration, you can only have 4 primary partitions. And if you want more, then one primary must be the extended partition to hold all your logical partitions.
Windows only installs in BIOS boot mode when drive is MBR.

If you have newer hardware (since 2012), then you have UEFI and can use gpt partitioning where all partitions are (in effect) primary. But then Windows only boots in UEFI boot mode.

Forcing conversion from MBR to gpt will normally erase drive. But you can use tools to convert, but have to reinstall grub and perhaps some other configuration settings. Often then better to have good backups and correctly install in UEFI boot mode to gpt drive.

Post this:
sudo parted -l

---

### Post by ow9ner on 2020-08-14
Thanks, fred. I have the '35 year old BIOS/MBR configuration. I typed in  'sudo parted -l' in command terminal and it looks like I have 1  extended partition, this having the largest file size and one logical  partition (the one which I've resized and want to select as a primary  partition). 

So, should I make 1 more partition?

---

### Post by QIII on 2020-08-15
Moved to General Help.

The Resolution Centre is for Administrator requests in reference to your user name, account status, etc, or to address concerns about the actions of the Forums Staff.

The tag line for the sub-forum reads (in part) thus:

> This is the place to contact a forum admin concerning problems with your forum account, to appeal moderator action, to request a thread be moved from the jail, or to file a complaint about forum harrassment or abuse.


---

### Post by oldfred on 2020-08-15
Wanted you to post your partitions, so we could see them.

But Windows in BIOS mode only boots from primary NTFS partition with boot flag. Part of reason we normally suggest installing Windows first.

---

