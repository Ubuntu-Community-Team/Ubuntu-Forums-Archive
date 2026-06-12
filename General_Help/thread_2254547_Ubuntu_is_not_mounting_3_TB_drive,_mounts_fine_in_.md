---
title: "Ubuntu is not mounting 3 TB drive, mounts fine in Windows 7 (dual boot)"
date: 2014-11-27
forum: General Help
---

### Post by TakerOfVita on 2014-11-27
I have a 3 TB data storage disk that I use regularly in Windows 7.  I have my system set up with dual boot.  I have my Ubuntu install on one disk, my Windows install on a raid 0 array with two disks, and the 3 TB drive with just media/other data.  When booting in Windows 7, I can access the 3 TB drive without any issues, it shows the full 2.7+ TB as space that I can use and I can access the files on the drive.  However, when I boot into Ubuntu, the drive does not show up as a mountable partition in the file explorer.  

Here is what I have looked at already:
Disk Utility shows the physical drive, but shows Partitioning as "Not Partitioned"
GParted shows the drive as 2.73 TiB of unallocated space

parted:
(parted) print devices                                                    
/dev/sda (1000GB)
/dev/sdb (3001GB)
/dev/sdc (1000GB)
/dev/sdd (1000GB)
/dev/sde (120GB)
/dev/mapper/pdc_ddgeeihjfd2 (2000GB)
/dev/mapper/pdc_ddgeeihjfd1 (105MB)
/dev/mapper/pdc_ddgeeihjfd (2000GB)
(parted) select /dev/sdb                                                  
Using /dev/sdb
(parted) print                                                            
Error: /dev/sdb: unrecognised disk label        


gdisk shows the following:
Type device filename, or press <Enter> to exit: /dev/sdb
Partition table scan:
  MBR: protective
  BSD: not present
  APM: not present
  GPT: not present

Disk /dev/sdb: 5860533168 sectors, 2.7 TiB
Logical sector size: 512 bytes
Disk identifier (GUID): 3CD355DA-4DA1-4D59-B573-
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 5860533134
Partitions will be aligned on 2048-sector boundaries
Total free space is 5860533101 sectors (2.7 TiB)

Number  Start (sector)    End (sector)  Size       Code  Name

Command (? for help): 



It is my understanding that there should be a GPT partition table, with a single NTFS partition taking up the entire drive.

The only reason I really noticed this is because I installed Windows 8 on a SSD, and in Windows 8 the drive does not show up correctly.  Windows does not mount the drive, and shows a 2048 GB partition of the type of GPT Protective Partition, then the remainder of the drive is shown as unallocated space.

Is there any reason that Windows 7 could read my drive, but neither Windows 8 or Ubuntu 12.04 could?  This is all on the same computer with the same hardware.  I will keep looking for a solution myself; however, any help would be appreciated.

---

### Post by carl4926 on 2014-11-27
Did you originally setup this drive with gdisk (which would be my recommendation)

---

### Post by TakerOfVita on 2014-11-27
I've been using the drive for a while, but I think I did the setup in windows 7 when I got the drive.

---

### Post by carl4926 on 2014-11-27
> **TakerOfVita said:**
> I've been using the drive for a while, but I think I did the setup in windows 7 when I got the drive.
Do you mean you have been using it in Ubuntu too?
But that this is a recent issue that just developed?

---

### Post by carl4926 on 2014-11-27
Might also be worth from win 7
Check it for errors
Then safely remove the drive
Then reboot and try in Ubuntu again

---

### Post by TakerOfVita on 2014-11-27
I rarely use my Ubuntu install, this is just the first time I've tried to access the 3 TB drive through Ubuntu.

---

### Post by carl4926 on 2014-11-27
> **TakerOfVita said:**
> I rarely use my Ubuntu install, this is just the first time I've tried to access the 3 TB drive through Ubuntu.

That it doesn't work in win8 is alarming to me

---

### Post by TakerOfVita on 2014-11-27
I used the verify tool in win7, and it went through and found no errors.  Checking in ubuntu, nothing has changed.

---

### Post by JeQhdMD on 2014-11-27
The GUID does not look valid for sdb.   Should be 5 groups of numbers, separated by dashes.   You can use gparted, to re-label the drive correctly (may need to put numbers in brackets also on some devices).  Win8 and Linux error checking may be preventing i/o access.

---

### Post by TakerOfVita on 2014-11-27
I removed the full GUID from the post because I wasn't sure how sensitive a GUID was to post on the internet, but now I feel like an idiot.  I tried renaming the volume in win7 since that post.  Here is what it gives now:

GPT fdisk (gdisk) version 0.8.1

Type device filename, or press <Enter> to exit: /dev/sdb
Partition table scan:
  MBR: protective
  BSD: not present
  APM: not present
  GPT: not present

Creating new GPT entries.


Command (? for help): p
Disk /dev/sdb: 5860533168 sectors, 2.7 TiB
Logical sector size: 512 bytes
Disk identifier (GUID): DD92EEEB-00BF-4C8E-A281-4FA20B8D4600
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 5860533134
Partitions will be aligned on 2048-sector boundaries
Total free space is 5860533101 sectors (2.7 TiB)

Number  Start (sector)    End (sector)  Size       Code  Name

Command (? for help):

---

### Post by oldfred on 2014-11-27
A few users with Windows tools just have formatted drives without partitioning. Then they do not work as most tools expect partitions. 
Drive then may be seen as a superfloppy as floppy drives do not have partitions.

How does Windows 7 show drive?

---

### Post by TakerOfVita on 2014-11-27
I can go look for specifics, but it shows it the same as my other drives.  It shows it with 2.7 TB space, I have been using it to store files and access files like any other drive.  It is only when I go through ubuntu 12.04 or win8 that it doesn't act like a drive.

---

### Post by JeQhdMD on 2014-11-28
After backing up data, a reformat via gparted to ntfs might be worth a try, . . . :???:

---

### Post by TakerOfVita on 2014-11-28
In windows 7, it is "Type: Basic, Partition Style: GUID Partition Table (GPT), Capacity 2861460 MB"
It has one NTFS partition taking up the entire drive. (2861459 MB)

I have just enough space on my other drives to move everything to them and format the 3 TB.  I'm moving everything now and will format the drive with gparted.

---

### Post by TakerOfVita on 2014-11-28
Reformatting the hard-drive through GParted made it visible in both win 8 and ubuntu.  I had just enough space on other drives to shuffle things around and save everything.  I was hoping there was a way to fix what I had, but this is fine too.  Thanks for the ideas, guys.

---

