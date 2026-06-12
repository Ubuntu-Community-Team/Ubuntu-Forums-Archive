---
title: "Installation doesn't detect partitions."
date: 2014-08-05
forum: General Help
---

### Post by martok_gonzalez on 2014-08-05
Hello, does this indicate a left over GPT table? or is another problem? And should I use FixParts to do the job?

Edit: Ok, i've attached the images.

---

### Post by oldfred on 2014-08-05
Please attach images using paper clip icon in advanced editor.
And if just text output, copy & paste text into forum. If longer text then use code tags ( # ) to preserve formatting and make it easier to review.

Post this:
sudo parted -l
sudo fdisk -l

---

### Post by martok_gonzalez on 2014-08-05
> **oldfred said:**
> Please attach images using paper clip icon in advanced editor.
And if just text output, copy & paste text into forum. If longer text then use code tags ( # ) to preserve formatting and make it easier to review.

Post this:
sudo parted -l
sudo fdisk -l

Ok, thanks for the reply, I attached the images as you say. Seems my account in imageshak has ended it's trial :P.

---

### Post by yancek on 2014-08-05
The images you post indicate the computer is running some version of windows and there are three windows partitions.  Whatever windows you have is using GPT partitioning and to get more accurate information it is telling you to use GParted rather than fdisk.

---

### Post by martok_gonzalez on 2014-08-05
Hi, yes I have a Windows 7 Ultimate x64 operating system, with two partitions made alredy, one for the OS and another for personal stuff/games. 

I have just opened GParted again, but in the moment it opens I get this warning message, wich I don't know how to answer.

Edit: Ok, I've fixed it. It was a left over GPT Table. I runned FixParts, wich showed me this message 

[COLOR=#000000]NOTICE: GPT signatures detected on the disk, but no 0xEE protective partition![/COLOR]The GPT signatures are probably left over from a previous partition table.
Do you want to delete them (if you answer 'Y', this will happen
immediately)? (Y/N):
And answered yes. I can boot to Windows, and now in the installation process Ubiquity does show the partitions.

---

### Post by oldfred on 2014-08-05
Windows installer in BIOS boot mode converts a drive that was gpt to MBR, but incorrectly leaves the backup gpt partition table. So fixparts is the best way to remove backup gpt partition table.

You can install Windows 7 in UEFI mode. From UEFI/BIOS menu you should get two boot options and how you boot installer is how it installs. One user said the DVD worked, but all the instructions I have seen were to copy DVD to flash drive and do some updates to make it UEFI capable.

If you have more than one drive you can have both Windows and Ubuntu in BIOS boot mode, but use gpt for Ubuntu. Ubuntu boots in either BIOS or UEFI from gpt if correct supporting partitions are on drive.

While BIOS is well known, there are some advantages to UEFI and gpt. But if you have it installed and working the way you want, I would not convert now unless you like experimenting and have good backups.
 GPT Advantages (older but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
UEFI Advantages
[http://askubuntu.com/questions/446968/legacy-vs-uefi-help](http://askubuntu.com/questions/446968/legacy-vs-uefi-help)

---

