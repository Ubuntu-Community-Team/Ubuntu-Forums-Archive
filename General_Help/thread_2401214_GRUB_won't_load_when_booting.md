---
title: "GRUB won't load when booting"
date: 2018-09-15
forum: General Help
---

### Post by elod12 on 2018-09-15
I am dual booting windows 10 and ubuntu(on my ssd and hdd).

I have no problems booting into ubuntu by changing the boot order in the BIOS however I can't access my windows 10 with the same method. Whenever my PC boots, It skips loading up GRUB and loads straight into Ubuntu. I have tried running boot-repair but It did not solve my problem. Ubuntu is set as number 1 in my boot priority list.

I could use some advice,

Thanks for reading.

( My boot info txt file is too big to upload here.)

---

### Post by kc1di on 2018-09-15
Are both windows and ubuntu installed in the same mode?  That is if win10 is install using UEFI and Ubuntu using legacy it will not work. 
They both have to be install in UEFI or Legacy mode. 

Does running ```
sudo update-grub
``` find the Win10 partition?
[this page ]("https://www.howtogeek.com/56958/htg-explains-how-uefi-will-replace-the-bios/")has a good explaination of the differences.

---

### Post by elod12 on 2018-09-15
My windows10 is legacy while my ubuntu is UEFI and the command did not find a win10 partition.
Should reinstalling windows in UEFI mode fix my boot ?
Also, can i format my win10 system drive and reinstall windows on it without losing data from my other drive on the same device?
Thanks for the help.

---

### Post by oldfred on 2018-09-15
You should always have good backups anyway as users can select wrong drive, or system can assume incorrect drive. 
If Windows is on sdb, it may install a boot file on sda and not know or care what is already there in effect erasing it.
Often safer to unplug any other drives. But UEFI may then forget UEFI boot entries & you have to recreate those with your Ubuntu live installer.

How you boot install media UEFI or BIOS is then how it installs, both Windows & Ubuntu.
Windows only installs in UEFI boot mode to gpt partitioned drives.
Windows only installs in BIOS boot mode to MBR partitioned drives.
And normal conversion like that erases entire drive, not just Windows partition.
Both Windows and Linux have tools to convert from MBR to gpt, but backup highly recommended.

And Windows has a different set of required partitions for UEFI. Scroll down for graphic view.
       BIOS & UEFI Windows partitions, note system has totally different format  & meaning between BIOS & UEFI
[https://msdn.microsoft.com/en-us/library/windows/hardware/dn898504%28v=vs.85%29.aspx](https://msdn.microsoft.com/en-us/library/windows/hardware/dn898504%28v=vs.85%29.aspx) & 
[https://msdn.microsoft.com/en-us/library/windows/hardware/dn898510%28v=vs.85%29.aspx#RecommendedPartitionConfigurations](https://msdn.microsoft.com/en-us/library/windows/hardware/dn898510%28v=vs.85%29.aspx#RecommendedPartitionConfigurations)

---

### Post by elod12 on 2018-09-16
I formated the drive and reinstalled windows in UEFI mode, now I can boot into both windows and ubuntu without a problem, although not with the assistance of GRUB, but the BIOS.(which is not an issue).

Thanks for helping me out in your own spare time!

---

### Post by kc1di on 2018-09-16
you should be able to fix grub. [This page ]("https://itsfoss.com/no-grub-windows-linux/")may be of help. good luck.

---

