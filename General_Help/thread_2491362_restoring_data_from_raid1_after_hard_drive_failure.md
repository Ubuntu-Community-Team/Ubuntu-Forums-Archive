---
title: "restoring data from raid1 after hard drive failure"
date: 2023-10-05
forum: General Help
---

### Post by asb3 on 2023-10-05
Several years ago I bought two WD usb hard drives.  
I intended to configure them as a RAID1. I might have not done it correctly.
Today I can't access the data.

If I plug in the drives and run lsusb, they show up:
> lsusb
[FONT=monospace][COLOR=#000000]Bus 004 Device 011: ID 1058:25a3 Western Digital Technologies, Inc. Elements Desktop (WDBWLG) [/COLOR]
Bus 004 Device 012: ID 1058:25a3 Western Digital Technologies, Inc. Elements Desktop (WDBWLG)

If I run lsblk, they show up, but they are not mounted:
>lsblk
[/FONT][FONT=monospace][COLOR=#000000]sde                   8:64   0   3.7T  0 disk   [/COLOR]
&#9492;&#9472;sde1                8:65   0   3.7T  0 part  

If I only plug in one of the drives, it shows up in lsusb, but not in lsblk.

If I try to mount the drive, I get an error:

[/FONT][FONT=monospace]
[/FONT]> sudo mount /dev/sde1 /mnt/data
mount: /mnt/data: wrong fs bypte, bad option, bad superblock on /dev/sde1, missing codepage or helper program, or other error.

running fdisk yields

> fdisk -l
Disk /dev/sde: 3.65 TiB, 4000752599040 bytes, 7813969920 sectors
Disk model: Elements 25A3   
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: gpt
Disk identifier: 40F89BD0-DF35-4524-9C87-04C2DBFC22A3

Device     Start        End    Sectors  Size Type
/dev/sde1   2048 7813967871 7813965824  3.7T Microsoft basic data


[FONT=monospace]
[/FONT]

---

### Post by TheFu on 2023-10-05
a) never use USB connected storage for RAID.
b) RAID still requires a backup.
c) whenever posting terminal output, please, please, please use forum code-tags, so the columns line up correctly.

HDDs fail all the time.  That's why we have backups.  RAID solves 2 issues - high-availability and (sometimes) improved performance.  This assumes you don't shoot your RAID system in the head with USB storage and still maintain proper backups.  If you don't have backups worked very well, there's no reason to have RAID.  Backups solve 1001 issues, including many RAID failures. RAID solves 2.

---

### Post by asb3 on 2023-10-05
I thought the purpose of a RAID is to supply a backup.
If I shouldn't use USB drives, how should I connect the external drives to the computer?
What are forum code tags?

Is there anything I should try that might help me get the data off the drives?

---

### Post by TheFu on 2023-10-05
> **asb3 said:**
> I thought the purpose of a RAID is to supply a backup.

Nope. That is incorrect. RAID is never a backup.
> **asb3 said:**
> 
If I shouldn't use USB drives, how should I connect the external drives to the computer?

I said you shouldn't use USB for RAID, not that you shouldn't use USB.  They are fine for backup use.

> **asb3 said:**
> 
What are forum code tags?

Code Tags: [Https://ubuntuforums.org/misc.php?do=bbcode#code](Https://ubuntuforums.org/misc.php?do=bbcode#code)


> **asb3 said:**
> 
Is there anything I should try that might help me get the data off the drives?
So, you don't have proper backups?

What options you have would depend on the type of RAID used.  mdadm? LVM?  ZFS? BTRFS? FakeRAID?

---

### Post by asb3 on 2023-10-06
I set it up using mdadm.

---

### Post by TheFu on 2023-10-06
First, you cannot mount the partition directly. It has RAID stuff that needs to be honored.  

So, the first step is to assemble the array in a degraded format.  There are guides for the specific command. Any **mdadm** tutorial can show those as well.  Take notes, so if you do choose to do RAID better next time, you have those notes for the recovery.  Having backups isn't optional, either, BTW.  Since the device name may need to change for this to work, it is best if you find a tutorial to understand that aspect.

After the array (degraded) is re-assembed, then you can try mounting the specific device.  That would be something like 

```
sudo mount /dev/md128 /mnt/RAID
```
Just change the device and location to match what you have.

Never use USB-connected disks for RAID.  The USB-storage and other USB drivers don't have the same control commands that a proper SATA/eSATA/SCSI/Infiniband connection has. USB isn't good for RAID, as you've learned the hard way.  Never use USB devices for primary storage, just for backups. If you add external storage devices as DAS, be certain they have excellent storage protocols and are clipped or screwed in connections.

---

