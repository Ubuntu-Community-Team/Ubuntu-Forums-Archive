---
title: "Grub does not seem to recognize Windows 10"
date: 2018-02-26
forum: General Help
---

### Post by ummaya on 2018-02-26
Hello,  

my previous System was:

a 1 TB drive with Windows 7 (partitioned into C and D)
a 2 TB drive with Ubuntu Mate 17.10


from several days ago my new setup is:

250GB SSD with Windows 10

1 TB drive (the previous Windows 7 drive) for files, movies, etc...

2 TB drive on which I installed Ubuntu Mate 17.10

I first installed Windows 10 on the 250 GB SSD while the 2 TB drive with Ubuntu Mate 17.10 was disconnected. I Booted into Windows to check if everything was OK and deleted the ex-Windows 7 install from the 1 TB drive.
To be sure to make no error, I disconnected the Windows 10 SSD and also the 1 TB drive and then I made a fresh installation of Ubuntu Mate 17.10 on the 2 TB drive and rebooted to check if the install was OK and then reconnected the SSD drive and the ex 'Windows drive' and then Windows 10 was booting automatically.

From the BIOS, I booted into Ubuntu Mate and ran "sudo update-grub" and then change the priority order in BIOS so it would search into Ubuntu Mate drive first. On reboot, grub appears but instead of Windows 10 and Ubuntu Mate options, I get **Windows 7** and Ubuntu Mate ( I deleted Windows 7, so I have no idea why it still appear in grub) I cannot boot into Windows 10 from grub, only from BIOS. Afterward, I ran  '*sudo grub-install /dev/sdc* ' ( C, the letter of my 'Ubuntu drive' ) and got the following message:  "**installing for i386-pc platform.Installation finished. No error reported**", then I ran '*sudo update-grub*' but nothing changed in grub.

I installed the Boot-Repair graphical tool and ran it and got the following message:  "*The current session is in Legacy mode. Please reboot the computer, and use this software in an EFI session. This will enable this feature. For example, use a live-USB of Boot-Repair-Disk-64bit ([www.sourceforge.net/p/boot-repair-cd](www.sourceforge.net/p/boot-repair-cd)), after making sure your BIOS is set up to boot USB in EFI mode*" 

Windows 10 on the SSD is installed in  UEFI mode.

I seems that it would be better if I re-install Ubuntu Mate in EFI mode (I did not pay attention if in which mode I installed Ubuntu) By the way, in my previous setup with Windows 7 installation, I did not encounter any of this UEFI-Legacy problem/grub problem
Which is the best way to install Ubuntu Mate in UEFI mode? Any link to a step by step clear description (easy for a noob) of this process?


Thank you very much.

---

### Post by oldfred on 2018-02-26
UEFI an BIOS are not compatible. You must choose boot mode when first booting and then cannot switch.
You should still be able to dual boot but only from UEFI boot menu, not grub as grub cannot switch to different boot mode.

How you boot install media, is how it installs for both Windows & Ubuntu.
Install for UEFI and BIOS is not really different except if installing to separate drive best to partition in advance using gpt and including the ESP - efi system partition as first partition. Or again disconnect Windows drives, so Ubuntu only sees the one drive. I still like to partition in advance and have ESP (FAT32) partition as first partition. Actually I like to have at least a smaller Ubuntu install on every drive even "just" data drives.

But if you disconnect UEFI drives, UEFI then forgets UEFI entires. Many systems do auto find Windows entries, but do not search for any others. Then you have to use efibootmgr to readd entries or reinstall grub (in UEFI mode) which also adds entries.

Lots of details in link in my signature.

 Shows install with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
Something Else or manual Install
[http://www.dedoimedo.com/computers/dual-boot-windows-8-ubuntu.html](http://www.dedoimedo.com/computers/dual-boot-windows-8-ubuntu.html)
Also shows Windows 10 screens or similar to Windows 8
[http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-windows-10-with-uefi](http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-windows-10-with-uefi)
UEFI install,windows 8 with Something Else screen shots, similar for newer versions of Ubuntu
[http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html](http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html)

---

### Post by ummaya on 2018-02-26
Thank you very much oldfred !

---

