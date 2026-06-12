---
title: "dual-boot: The partitions have gone haywire, can't boot"
date: 2016-07-05
forum: General Help
---

### Post by avi.sharma on 2016-07-05
Hey friends! 
My setup: Lenovo G510, 4GB RAM, Core i5 4th Gen, 500GB HDD, Windows 10 64bit + Ubuntu dual boot (C is the primary drive with windows on it and gets around 120GB, E has the rest minus 15GB for Ubuntu)

So here is what happened: I came back from work last week and saw the infamous grub rescue error greeting me instead of the normal OS selection screen. I was in a hurry and considering the fact that my Ubuntu was still to be setup properly and I had easy access to a windows recovery USB, I went to the recovery command prompt and ran the fixmbr and fixboot commands. Worked like a charm, I was in Windows and finished my work. 

I opened the disk management section on Windows to wipe the partition clean and start with a fresh install of ubuntu on a new partition, but to my surprise it was not shown there. Nevertheless, I created a new 15GB partition for Ubuntu and booted the ubuntu live USB to start with the new install. However, it did not show me any partition at all! Just the complete drive with no free space. I referred some forums online and saw that it might be residual matter from the previous installation but I was not sure how to locate this partition to wipe it. Some forums indicated that the partition table needs rebuilding. I thought thats weird for the laptop was still detecting my HDD and Windows did show the partitions currently. Probably a format mismatch between the two OSs. I used the bootrepair disk live USB utility to try and fix the grub but that did not work either. 

Fastforward to a few days I was on the Ubuntu installer again (made a new USB) and tried to install once more. I remember selecting Erase all content and LVM option and by mistake clicking continue. A popup warned me about the changes that were supposed to occur and I quickly retraced my steps from there. However, now I cannot boot into Windows either! I get the message: No bootable device found, please connect a bootable device and press any key ...". I checked the BIOS menu  to see if the HDD is still there and running, and yes it is being  detected. I still think this is some partitioning / partitioning format  problem. Can we build the partition table again to access the data again? Please check the screenshots for more information. 

**Goal: **Try  and restore data from E drive. I can let go of the data in C drive. Fix  the partitions and have a working laptop again. Thanks :)

[ATTACH=CONFIG]269964[/ATTACH][ATTACH=CONFIG]269965[/ATTACH][ATTACH=CONFIG]269966[/ATTACH][ATTACH=CONFIG]269967[/ATTACH][ATTACH=CONFIG]269968[/ATTACH]

**Update 5/7/16:** Living like a nomad from one Live USB to the next. Couldn't manage to make a persistent live media via Unetbootin (doesn't boot at all, syslinux error). I think one way to fix this problem would be to rebuild the partitions from scratch and in the process, painfully wiping all my data. Please dont make me do this to ***Arwen*** :(

---

### Post by banceu_sergiu_ione on 2016-07-05
Hi 
Can you put the output of ```
sudo parted -l
```

---

### Post by avi.sharma on 2016-07-05
> **banceu_sergiu_ione said:**
> Hi 
Can you put the output of ```
sudo parted -l
```

```
ubuntu@ubuntu:~$ sudo parted -l
Model: ATA WDC WD5000LPCX-2 (scsi)
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos
Disk Flags: 

Number  Start   End    Size   Type      File system  Flags
 1      1049kB  512MB  511MB  primary   ntfs
 2      513MB   500GB  500GB  extended
 5      513MB   500GB  500GB  logical                lvm


Model: Kingston DataTraveler 2.0 (scsi)
Disk /dev/sdb: 7747MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start   End     Size    Type     File system  Flags
 1      1049kB  7747MB  7746MB  primary  fat32        boot, lba


Error: /dev/mapper/ubuntu--vg-swap_1: unrecognised disk label
Model: Linux device-mapper (linear) (dm)                                  
Disk /dev/mapper/ubuntu--vg-swap_1: 4203MB
Sector size (logical/physical): 512B/4096B
Partition Table: unknown
Disk Flags: 

Error: /dev/mapper/ubuntu--vg-root: unrecognised disk label
Model: Linux device-mapper (linear) (dm)                                  
Disk /dev/mapper/ubuntu--vg-root: 495GB
Sector size (logical/physical): 512B/4096B
Partition Table: unknown
Disk Flags: 


```

---

### Post by yancek on 2016-07-05
> I remember selecting Erase all content and LVM option and by mistake clicking continue

The output of the parted -l command you posted indicates that is exactly what happened.  It erased everything as it said it would.  Also, an LVM install will overwrite whatever you have on the computer.  You have overwritten your windows installation, at least everything except what looks like an EFI partition (sda1).  I hope you have a windows installation DVD if you still want it.  If you have data on the windows partition, you might be able to save it with testdisk.

---

### Post by avi.sharma on 2016-07-05
> **yancek said:**
>   If you have data on the windows partition, you might be able to save it with testdisk.
Oh noes. Are you sure there is no way to recover the data? Like even if I detach the harddrive and show it to a technician? (I dont think the data is worth the cost of a professional data recovery process so I'm just hinting at basic recovery procedures by a technician).

 I dont think there's much left on that small Windows EFI partition but if you could point me to the testdisk procedure to do so that'd be great. 

Also could you please advise on how to proceed with this HDD for a new install? Should I use Gparted to format the drive and build a new partition table? What are those vg-root drives? I dont want to ruin my HDD. 

Lastly, is it safe to say clicking continue in the Ubuntu installer after selecting erase all content and LVM before the final confirmation will still erase all my data?

---

### Post by oldfred on 2016-07-05
You will not be able to recover a bootable system as at least parts of Windows were overwritten with the full drive install.
But testdisk may see old partitions and deeper search find files. Not all may be complete.
Or Ubuntu is not large and does write to entire drive randomly and Windows typically writes to start of drive, so only some data overwritten.
Photorec which is part of testdisk can scan entire drive for anything that looks like a file, but only finds extensions, not full file name. Took me weeks to sort, and compare older backup files to recovered files. Photorec also recovers deleted files.

       [https://askubuntu.com/questions/286181/how-do-i-recover-my-accidentally-lost-windows-partitions-after-installing-ubuntu](https://askubuntu.com/questions/286181/how-do-i-recover-my-accidentally-lost-windows-partitions-after-installing-ubuntu)
Testdisk Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)
[URL="http://www.cgsecurity.org/wiki/TestDisk:_undelete_file_for_NTFS"]http://www.cgsecurity.org/wiki/TestDisk:_undelete_file_for_NTFS
[/URL]
 Testdisk & photorec
[http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)
[http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step](http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step) 
      
 gddrescue, Scalpel, magic rescue, photorec, foremost, sleuthkit & others
[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery) 
    
Some say Windows tools work better for NTFS file structures:

 An alternative Windows data recovery program is Recuva -- and it is free
[http://ubuntuforums.org/showthread.php?t=2247461](http://ubuntuforums.org/showthread.php?t=2247461)
[http://ubuntuforums.org/showthread.php?t=2236951&p=13086950#post13086950](http://ubuntuforums.org/showthread.php?t=2236951&p=13086950#post13086950)
You could start by using Recuva -- to see what it finds. If it doesn't work, you should then try RecoverMyFiles -- to see what it finds.
NTFS file recovery suggestion by Mark Phelps (not free but works)
[http://ubuntuforums.org/showpost.php?p=12490412&postcount=4](http://ubuntuforums.org/showpost.php?p=12490412&postcount=4)
For NTFS but may charge to actually get your data, but can run to see if it works better.
[http://ubuntuforums.org/showthread.php?t=2193293](http://ubuntuforums.org/showthread.php?t=2193293)
[http://ubuntuforums.org/showthread.php?t=2221353&p=13010810#post13010810](http://ubuntuforums.org/showthread.php?t=2221353&p=13010810#post13010810)
[http://www.getdata.com/](http://www.getdata.com/)
For NTFS - GetDataBack often recommended
Caution: getdataback is not the same and is a scam.

---

### Post by avi.sharma on 2016-07-05
Thank you so much for the resources.

I will run the tools for recovery but don't really have high hopes. I dont mind the data loss it was mostly movies and music so thats alright. However, I do want the laptop to return to a working condition and want to do so without damaging my drive with some disk operation. Should I format these partitions and start with a clean windows and subsequently ubuntu install? Or do I have to do something to these partitions first as in building the partition table or something else? Really confused.

---

### Post by banceu_sergiu_ione on 2016-07-05
> **avi.sharma said:**
> Thank you so much for the resources.

I will run the tools for recovery but don't really have high hopes. I dont mind the data loss it was mostly movies and music so thats alright. However, I do want the laptop to return to a working condition and want to do so without damaging my drive with some disk operation. Should I format these partitions and start with a clean windows and subsequently ubuntu install? Or do I have to do something to these partitions first as in building the partition table or something else? Really confused.

If you don't mind data lose, then format your HDD and start with a clean install. You can let the installer to format for you or you can use gpart to format and partitioning your disk as you like. I would recommend to do only what you know and what is easier for you. If you're not completely aware of what LVM is and know how it work, I would suggest to go for an install without LVM or read more about it before to chose it.

---

### Post by oldfred on 2016-07-05
Was system originally Windows 10 and therefore UEFI with gpt partitioing? Or an upgrade from Windows 7 and probably BIOS with MBR partitioning.

How you boot install media for both Windows & Ubuntu is then how it installs. Or if you boot in UEFI mode it installs in UEFI mode and you have to boot system in UEFI mode.
Windows only boots from gpt partitioned drives with UEFI. 

 How to: Create a Recovery Drive for reinstalling Windows 10 from Windows 10
[http://answers.microsoft.com/en-us/windows/wiki/windows_10-win_upgrade/how-to-create-a-recovery-drive-for-reinstalling/58df9c7d-84de-4652-9952-8bac34abc6c5](http://answers.microsoft.com/en-us/windows/wiki/windows_10-win_upgrade/how-to-create-a-recovery-drive-for-reinstalling/58df9c7d-84de-4652-9952-8bac34abc6c5)
Repair/backup/restore
[http://windows.microsoft.com/en-us/windows-10/windows-10-recovery-options](http://windows.microsoft.com/en-us/windows-10/windows-10-recovery-options) 
Windows 10 ISO
[https://www.microsoft.com/en-us/software-download/windows10ISO](https://www.microsoft.com/en-us/software-download/windows10ISO)
Windows 10 repair disk
[http://www.tenforums.com/tutorials/36083-system-repair-disc-create-windows-10-a.html](http://www.tenforums.com/tutorials/36083-system-repair-disc-create-windows-10-a.html)

Since your hardware is UEFI, you should review the link below in my signature. It is a lot of data but some is vital to understanding UEFI and UEFI installs.

---

