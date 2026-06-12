---
title: "Boot repair - Boot partition cant be selected-"
date: 2018-04-26
forum: General Help
---

### Post by loofy14598 on 2018-04-26
Hi team


On a Ubuntu 16.04 freshly installed that wouldnt turn on at all anymore

I followed the Boot repair procedure=



_Boot successfully repaired._

_A new file (/var/log/boot-repair/20180410_013533/Boot-Info_20180410_0135.txt) will open in your text viewer._



_You can now reboot your computer._



_The  boot files of [The OS now in use - Ubuntu 16.04.4 LTS] are far from the  start of the disk. Your BIOS may not detect them. You may want to retry  after creating a /boot partition (EXT4, >200MB, start of the disk).  This can be performed via tools such as gParted. Then **select this partition via the [Separate /boot partition:]** option of [Boot Repair]. (__[https://help.ubuntu.com/community/BootPartition](https://help.ubuntu.com/community/BootPartition)_[U])
[IMG]https://ubuntuforums.org/blob:https://mail.protonmail.com/f1d2ac39-cfd3-43bb-82e9-21556ba674bc[/IMG]
[/U]

[IMG]https://ubuntuforums.org/blob:https://mail.protonmail.com/f1d2ac39-cfd3-43bb-82e9-21556ba674bc[/IMG]
Now the thing is

I cant enable this option
The only option available as shown on the picture is
- OS to boot by default= sda1 -
- Place GRUB into= sda-


[IMG]https://ubuntuforums.org/blob:https://mail.protonmail.com/f1d2ac39-cfd3-43bb-82e9-21556ba674bc[/IMG]



Sorry  if I missed a step, I am new to Ubuntu and now I can barely boot in recovery modem what can I do to run it normally
 thanks for your  help,



Regards,



Loofy



Detailed pastebin herewith

[http://paste.ubuntu.com/p/CDtMCrHPnf/](http://paste.ubuntu.com/p/CDtMCrHPnf/)

---

### Post by yancek on 2018-04-26
The image you posted isn't useful.  You should post the link you were given after running boot repair which will provide a lot of details.  You don't mention any other operating system so I'm curious as to why you installed Ubuntu at the end of the disk?   Which installation type option did you choose, the Erase Disk and install Ubuntu or another option?  Also, do you know if you selected to insatll using UEFI or Legacy/CSM?  How old is your hardware?

---

### Post by oldfred on 2018-04-26
Its is just a warning that Boot-Repair gives. Boot-Repair will use a separate /boot partition if you have one, but separate /boot not normally recommended for new installs with newer hardware.

Old BIOS' had a limit on where boot files could be on drive. Most recent limit was 137GB. Or boot files on drive had to be within the first 137GB. Some newer BIOS when drives were in the old IDE mode for compatibility seemed to show same issue. But BIOS now should be using AHCI to access drives not IDE, nor RAID.
And issue was solved by totally repartitioning with /boot partition at beginning. Or shrinking a system like yours so / (root) which has the /boot folder and then all boot files are totally within the first 100GB of drive. Then rest of drive is available for /home partition or data partition(s).

But after all that all new UEFI systems using gpt partition the warning does not apply. Or all systems in last 5 years as they are UEFI.  When Windows 8 was released in 2012, Microsoft requried all vendors to use UEFI with gpt partitioning.

It looks like you have a newer UEFI system, but installed in the now 35 year old BIOS/MBR configuration. Ubuntu also can boot from newer gpt partitioning if you include correct supporting partition. And Windows in UEFI mode only boots from gpt or only boots in BIOS mode from MBR(msdos).

Check that UEFI/BIOS is using AHCI, not RAID nor IDE.

We often suggest 25GB for / (root) and rest of drive for /home and/or data partitions.

       GPT Advantages (older 2010 but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT) 
    
If you want to re-install, I would suggest this for partitions:
       For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap(prior to 17.10), but it is better to add another partition for /home if allocating over 30GB.:
Only if gpt -  all partitions in gpt are primary (no logicals):
gpt: 300-500 MB efi FAT32 w/boot flag (ESP for UEFI boot or future use for UEFI, you only can have one per drive, so if already existing do not attempt another)
gpt: 1 or 2 MB No Format w/bios_grub flag (for BIOS boot not required for UEFI)
for gpt(GUID) or MBR(msdos) partitioning
Ubuntu partitions - smaller root only where hard drive space is limited.
If total space less than about 30 to 50GB just use / not separate /home or standard install.


[LIST=1]
[*]25-30+ GB Mountpoint / primary or logical beginning ext4
[*]all but 2 GB Mountpoint /home logical beginning ext4
[*]2 GB Mountpoint swap logical (not required with 17.04 and later uses a swap file, if no swap partition found)
[/LIST]
    Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)

---

