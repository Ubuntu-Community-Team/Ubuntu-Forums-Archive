---
title: "New computer, want some general partitioning advice"
date: 2018-05-22
forum: General Help
---

### Post by maeldun2 on 2018-05-22
Hey, I have a new computer coming in shortly and I want to switch to Linux (again....). I'll be using a Ryzen 2200g processor and it's Vega graphics. I want to try a few linux distros to see which one I like the most. I'll be starting with Xubuntu and either mint or Solus. Because the Ryzen 2200g is still pretty unusable at the moment (from what I've read) I'll also want to have a backup windows boot while I'm waiting for more support for the 2200. A little advice on partition sizes would be greatful, as I'll only have a 250G SDD to start with. My initial idea is as follows:

1. Xubuntu partition
2. mint/Solus
3. WindowsXP 
4. /Home partition to be shared by linux distros
5. Potential spare partition for games (or shall I just lump them in under home?)

As space is tight, I'd appreciate knowing what's the absolute minimum (but still with a little wiggle room) space needed for these OS partitions. I also forgot the swap partition didn't I....

---

### Post by oldfred on 2018-05-22
Do not share /home.
Do not use XP, you then become a virus magnet as Microsoft does not support it any more and it was not the best for security when it was supported. 
Also do not think XP could be installed in UEFI mode. Windows 7 default is BIOS, but can be converted to UEFI installer if copied to a flash drive and slightly modified.
Also if drive is an SSD, you have to use AHCI for drive, but XP only works with the older IDE. I retired XP as I was down to one app, and my first tiny SSD required me to change to AHCI. Going into BIOS to change every time was the straw that broke the camels back. 

I have multiple Ubuntu installs and use 25GB for each for / (root) with /home inside /. But have all my data in a /mnt/data partition which I can easily mount & use in every install. Then I do not have to worry about any conflicts in user settings from /home as I keep it inside / (root) partition.

With new UEFI system best to take advantage of UEFI with gpt partitioning. 

All versions of Windows only boot in BIOS mode from MBR partitioning and only with UEFI from gpt partitioning.
And how you install Windows determines partitioning so the Ubuntu needs to be in same boot mode.

       GPT Advantages (older 2010 but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
[http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface)
[http://askubuntu.com/questions/629470/gpt-vs-mbr-why-not-mbr](http://askubuntu.com/questions/629470/gpt-vs-mbr-why-not-mbr)
UEFI Advantages
[http://askubuntu.com/questions/647303/uefi-or-legacy-which-is-advised-and-why/647604#647604](http://askubuntu.com/questions/647303/uefi-or-legacy-which-is-advised-and-why/647604#647604)
[http://askubuntu.com/questions/446968/legacy-vs-uefi-help](http://askubuntu.com/questions/446968/legacy-vs-uefi-help) 
    
       Shows install with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

You may need to add ppa's to get newer kernels to make it work. 
       Ubuntu 18.04 with updates from ppas
Ryzen 7 2700 / Ryzen 7 2700X / Core i7 8700K Linux Gaming Performance With RX Vega 64, GTX 1080 Ti
[https://www.phoronix.com/scan.php?page=article&item=ryzen-2700-gaming&num=1](https://www.phoronix.com/scan.php?page=article&item=ryzen-2700-gaming&num=1)

---

### Post by maeldun2 on 2018-05-23
Wow, very detailed, thank you, but I don't understand most of it. If I have to scrap my idea of using win XP, ok fine.... But the rest I just don't understand.

I was just giong to install Xubuntu, use that to partition my whole drive, and then install windows on the appropriate drive. Is that not going to work? (Let's assume windows 7)

---

### Post by oldfred on 2018-05-23
Generally best to install Windows first. It wants differnent partition layouts depending on if UEFI or BIOS.
       BIOS & UEFI Windows partitions, note system has totally different format  & meaning between BIOS & UEFI
[https://msdn.microsoft.com/en-us/library/windows/hardware/dn898504%28v=vs.85%29.aspx](https://msdn.microsoft.com/en-us/library/windows/hardware/dn898504%28v=vs.85%29.aspx) & 
[https://msdn.microsoft.com/en-us/library/windows/hardware/dn898510%28v=vs.85%29.aspx#RecommendedPartitionConfigurations](https://msdn.microsoft.com/en-us/library/windows/hardware/dn898510%28v=vs.85%29.aspx#RecommendedPartitionConfigurations) 
    
But with Windows you must pay attention to boot mode as that determines whether install is UEFI or BIOS and whether partitioning is MBR or gpt.
       Convert Windows 7 install to UEFI This user said he need the repair/recovery from his Windows 8 to convert Windows 7
[http://ubuntuforums.org/showthread.php?t=2304736](http://ubuntuforums.org/showthread.php?t=2304736)
        How to Create a Bootable UEFI USB Flash Drive for Installing Windows 7, Windows 8, or Windows 8.1 - Also command line install of files to efi partition uses rufus
[http://www.eightforums.com/tutorials/15458-uefi-bootable-usb-flash-drive-create-windows.html](http://www.eightforums.com/tutorials/15458-uefi-bootable-usb-flash-drive-create-windows.html)
[https://superuser.com/questions/676249/clean-install-of-windows-7-pro-64-bit-on-a-uefi-laptop-with-gpt-partition](https://superuser.com/questions/676249/clean-install-of-windows-7-pro-64-bit-on-a-uefi-laptop-with-gpt-partition) 
    [http://social.technet.microsoft.com/wiki/contents/articles/14286.converting-windows-bios-installation-to-uefi.aspx](http://social.technet.microsoft.com/wiki/contents/articles/14286.converting-windows-bios-installation-to-uefi.aspx)

You generally cannot use an install to edit partitions as partitions are mounted. I do use gparted in my install to partition sdb or flash drives, but not sda.
You can use the live installer or also have a live version of gparted.
 
With one of my motherboards, I must have had 8 or 10 UEFI settings to change. My most recent build only needed several.
You need to turn off UEFI Secure boot. My system called it "Windows" or "Other". But fine print said you had to use "Other" with Windows 7 as Windows 7 does not support UEFI Secure Boot, but can boot in UEFI mode. So "Other" is really UEFI secure boot off.
Better to turn UEFI fast boot off, otherwise you may not have time to press keys to get into UEFI to change settings. UEFI fast boot assumes system  has not changed, either hardware nor software configuration, and immediately jumps to booting.
You may need to turn on allow USB boot and make sure drives are AHCI, not RAID nor IDE.
Every brand seems to have something unique, but almost all systems will work.

---

### Post by maeldun2 on 2018-05-23
Ok, I've done a bunch of reading and I think I'm following you now. Thanks a lot for your help, during my setup if and when things go wrong, I'll already have an idea of  what to check. Thanks a lot.

Any idea how big I should make the windows partition?

edit: also, I've got way too much RAM (16g, definitely only needed 8g), can I skip the swap partition?

---

### Post by oldfred on 2018-05-23
Ubuntu now uses swap file. It will use a swap partition if you have one, but not now needed.
See changes since 16.04
[https://wiki.ubuntu.com/BionicBeaver/ReleaseNotes](https://wiki.ubuntu.com/BionicBeaver/ReleaseNotes)

How big is hard drive? How much data are you going to save in Windows. Are you planning a shared NTFS partition for some or most of Windows data?
My only Windows is 100GB, but needed more space to upgrade from Windows 8 to 10.
But NTFS only works well if you have 30% free inside the NTFS partition. At 20% it starts to slow and at 10% a defrag may take forever.

---

### Post by maeldun2 on 2018-05-27
My hard drive is 250GB. I wanted to have a partition for each OS so that if I choose to replace/remove it (windows definitely on the chopping block in the future), and a seperate partition for my data so that regardless of what happens to my OS, I won't lose my stuff. Most of the data is going to be taken by games, my other programs won't need nearly as much. Also some media files, but if they become an issue I can store them on an external drive.

Does windows operate better on NTFS as opposed to Fat3? NTFS just sounds like a poor format, I'd rather not use it at all unless I'm missing something here.

Is 20GB for an OS not enough? I was thinking of a 20(Linux1)/20(Linux2)/20?(Windows7)/~190GB(The rest) split.

---

### Post by oldfred on 2018-05-27
FAT32 is only for smaller partitions like ext2 is for smaller partitions. Neither has journal, so more difficultor impossible to resolve errors. FAT32 also cannot store large files.

 Now old as your should use NTFS not FAT32
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)
[http://ubuntuforums.org/showthread.php?t=416802&p=12573520#post12573520](http://ubuntuforums.org/showthread.php?t=416802&p=12573520#post12573520)
[http://en.wikipedia.org/wiki/Disk_partitioning](http://en.wikipedia.org/wiki/Disk_partitioning)

I use 25 or 30GB for each install unless on a smaller flash drive where I do not do a lot of additional programs. Full install to flash drive is more for emergency boot.

My one Windows system has 100GB. But I needed a lot of extra room to upgrade from Windows 8 to Windows 10. And NTFS needs 30% free to work well, so do not make NTFS partitions too small.

This is my current 16.04 with my other installs also mounted.
```
fred@Xenial_z97:~$ df -h
Filesystem      Size  Used Avail Use% Mounted on
udev            3.9G     0  3.9G   0% /dev
tmpfs           793M  9.6M  784M   2% /run
/dev/sda6        24G  7.9G   15G  35% /
tmpfs           3.9G   35M  3.9G   1% /dev/shm
tmpfs           5.0M  4.0K  5.0M   1% /run/lock
tmpfs           3.9G     0  3.9G   0% /sys/fs/cgroup
tmpfs           3.9G  1.1M  3.9G   1% /tmp
/dev/sda1       500M   53M  447M  11% /boot/efi
/dev/sdb4       385G  131G  235G  36% /mnt/data
tmpfs           793M  120K  793M   1% /run/user/1000
/dev/sdd2        21G  5.9G   14G  31% /media/fred/bionic64usb
/dev/sdd3        36G   32G  2.5G  93% /media/fred/data64
/dev/sda7        29G  6.7G   20G  26% /media/fred/bionic
/dev/sdb8        25G  8.5G   16G  36% /media/fred/debian
/dev/sdb10       24G  4.7G   19G  21% /media/fred/mate
/dev/sda3        24G   13G   10G  57% /media/fred/trusty
/dev/sdb3        24G  6.4G   17G  29% /media/fred/xenial_b
```

Many are just test installs, with little updates.

---

### Post by SL0ltMJGyh on 2018-05-27
Your /home partition is not meant to be shared. Ideally, you want to create a partition scheme where your mount point is / and you install the home directory there. You also may wish to create a separate swap partition (I wouldn't, but you might depending on RAM). Also, replace Windows XP completely. The number of known holes in the OS are as numerous as grains of sand.

---

### Post by maeldun2 on 2018-05-30
Hey just wanna say thanks to oldfred and apmarek for helping me. After a lot of head aches, I ended up just going with windows 10..... windows 7 was way too hard to install because it doesn't have very good uefi support. The advice/information about uefi and gpt partitioning was very useful. I'm dual booting right now (got rid of xubuntu, xfce is nothing to write home about), using Ubuntu and Win 10. Plenty of spare space to add more distros if I want to try them out or do whatever.

Thanks again!

---

