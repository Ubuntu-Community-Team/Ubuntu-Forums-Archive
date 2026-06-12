---
title: "NTFS recovery Error"
date: 2016-03-06
forum: General Help
---

### Post by RocketPenguin on 2016-03-06
After running sudo ntfsfix on an NTFS partition that is supposedly broken, according to Gparted, i get this error:

```
Mounting volume... ntfs_mst_post_read_fixup_warn: magic: 0x00070007  size: 1024   usa_ofs: 40  usa_count: 7: Invalid argument
Record 0 has no FILE magic (0x70007)
Failed to load $MFT: Input/output error
FAILED
Attempting to correct errors... ntfs_mst_post_read_fixup_warn: magic: 0x00070007  size: 1024   usa_ofs: 40  usa_count: 7: Invalid argument
Record 0 has no FILE magic (0x70007)
Failed to load $MFT: Input/output error
FAILED
Failed to startup volume: Input/output error
Checking for self-located MFT segment... ntfs_mst_post_read_fixup_warn: magic: 0x00070007  size: 1024   usa_ofs: 40  usa_count: 7: Invalid argument
OK
ntfs_mst_post_read_fixup_warn: magic: 0x00070007  size: 1024   usa_ofs: 40  usa_count: 7: Invalid argument
Record 0 has no FILE magic (0x70007)
Failed to load $MFT: Input/output error
Volume is corrupt. You should run chkdsk.
```


What do?
When i run the command on the extended partition it is in, I get this error:
```
Mounting volume... NTFS signature is missing.
FAILED
Attempting to correct errors... NTFS signature is missing.
FAILED
Failed to startup volume: Invalid argument
NTFS signature is missing.
Trying the alternate boot sector
Unrecoverable error
Volume is corrupt. You should run chkdsk.

```

This was originally a windows partition that i managed to break with TestDisk.

Also, side question, another partition that was on this hdd has disappeared. How do i get it back? Gparted just shows empty space where it should be.

Gparted error:
```
ntfs_mst_post_read_fixup_warn: magic: 0x00070007  size: 1024   usa_ofs: 40  usa_count: 7: Invalid argument
Record 0 has no FILE magic (0x70007)
Failed to load $MFT: Input/output error
Failed to mount '/dev/sda5': Input/output error
NTFS is inconsistent. Run chkdsk /f on Windows then reboot it TWICE!
The usage of the /f parameter is very IMPORTANT! No modification was
made to NTFS by this software.

Unable to read the contents of this file system!
Because of this some operations may be unavailable.
The cause might be a missing software package.
The following list of software packages is required for ntfs file system support:  ntfsprogs / ntfs-3g.
```
Gparted screenshot: [http://imgur.com/7LldEka](http://imgur.com/7LldEka)

---

### Post by oldos2er on 2016-03-06
Have you done this? > NTFS is inconsistent. Run chkdsk /f on Windows then reboot it TWICE!

---

### Post by RocketPenguin on 2016-03-06
Can't. Windows won't boot, at all. When I turn on the machine (Without livecd), it tells me it cannot find a boot device. (Boot device not found, press enter. Or something like that.)

The partitioning looks wrong too. What I think i did, was when i used TestDisk, i scanned the C partition, and ended up putting it into another partition/extended. (Not sure, don't know too much about partitions/recovery. More into networking)

It sure doesn't look like my machine's partition table.

The partition IS the same size, so at least there's that...

---

### Post by RocketPenguin on 2016-03-06
Thing is, this partition didn't have too much on it. I'm more worried about the OTHER partition that disappeared... I'm hoping I can find it once windows is back (Or, for all I know, I'm making it worse by writing to the HDD. TestDisk doesn't see anything any more, other than the Extended partition, and the one partition in it, which is supposedly windows...)

---

### Post by oldfred on 2016-03-06
Windows will not boot from logical partition. You possibly can have a Windows install in a logical partition, but all boot files must still be in a primary NTFS partition with boot flag.

Do you have any backup of partition table, Boot-Repair summary report or anything that would show your exact partition layout as it was.
Post this to see where you are now.

       sudo parted /dev/sda unit s print

---

### Post by RocketPenguin on 2016-03-06
```
Model: ATA WDC WD4000AAKS-2 (scsi)
Disk /dev/sda: 781422768s
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start  End         Size        Type      File system  Flags
 1      19s    105467935s  105467917s  extended               lba
 5      63s    105466724s  105466662s  logical   ntfs

```

Unfortunately, no. I should have backed at least the important partition up, but i was lazy. Never again.

Any way to get rid of the logical table without formatting the partition inside of it? I highly doubt it was a logical partition before i messed it up... (Was a standard windows install with an extra partition made for storage... in case something like this would happen... except, that partition wasn't suppose to disappear/get damaged...)

---

### Post by oldfred on 2016-03-06
You can use fixparts or testdisk to change to primary, but if chkdsk will not run on it, you may need to use testdisk to either restore the backup PBR - partition boot sector or use it to create a new BS boot sector that is NTFS type. I think it makes an XP type, but then chkdsk from a newer version of Windows will update it. Main difference is inside NTFS PBR is either ntldr to boot XP or bootmgr to boot all versions after XP. But you must have the PBR or Windows thinks it is unformatted or RAW.

 [http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

---

### Post by RocketPenguin on 2016-03-07
I ran CHKDSK on a windows install CD, and i got this: [http://imgur.com/Vc3g3qD](http://imgur.com/Vc3g3qD)
How do I turn the logical partition into a primary one? I can't seem to figure this out.

---

### Post by oldfred on 2016-03-07
Fixparts can change logical to primary, but I have not done it. Link is above.
There are a lot of rules on partitions, and it follows those, so not all changes can be done.

---

### Post by RocketPenguin on 2016-03-07
UPDATE: Problem is fixed. Used TestDisk to convert partition to Primary.
This resolved all problems, and windows booted without error.

---

