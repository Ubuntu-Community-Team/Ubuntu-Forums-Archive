---
title: "gdisk MBR not present"
date: 2013-07-13
forum: General Help
---

### Post by scambro on 2013-07-13
I was formatting/ partitioning a drive in a NAS today, a single drive that had old data on it, but nothing that I cared about, just to get the NAS on.  I tripped the power in the middle of the process, it was probably 2 or 3 hours in, but there was not status percentage at all showing.  So I took the drive to my Ubuntu box, hooked it up, planning on wiping the partition and starting over.  It seems to be fairly well jacked up now and I can't seem to get it back... 

When I run gdisk on the device, I see this:

```

Warning! Read error 5; strange behavior now likely!
Warning! Read error 5; strange behavior now likely!
Partition table scan:
  MBR: not present
  BSD: not present
  APM: not present
  GPT: not present

Creating new GPT entries.

```

It doesn't seem to actually create the GPT tables though.  When I try straight up in parted, I get this:

```

:~$ sudo parted /dev/sdd
GNU Parted 2.3
Using /dev/sdd
Welcome to GNU Parted! Type 'help' to view a list of commands.
(parted) mklabel gpt                                                      
Error: Input/output error during read on /dev/sdd                         
Retry/Ignore/Cancel?     

```

With sfdisk, I get this:

```

Do you want to write this to disk? [ynq] y
read: Input/output error

sfdisk: read error on /dev/sdd - cannot read sector 0
Re-reading the partition table ...
BLKRRPART: Input/output error

If you created or changed a DOS partition, /dev/foo7, say, then use dd(1)
to zero the first 512 bytes:  dd if=/dev/zero of=/dev/foo7 bs=512 count=1
(See fdisk(8).)
:~$ dd if=/dev/sdd of=/dev/sdd1 bs=512 count=1
dd: opening `/dev/sdd': Permission denied
:~$ sudo dd if=/dev/sdd of=/dev/sdd1 bs=512 count=1
dd: reading `/dev/sdd': Input/output error
0+0 records in
0+0 records out
0 bytes (0 B) copied, 1.8923 s, 0.0 kB/s
:~$ 

```

As far as I can tell, the drive was in fine shape prior to the power cut.  I have two of the same drives partitioned with ext4 and spinning just fine.  If the partition tables are messed up, is there a way I can "copy" from the two working drives?  There is 0 data on this drive that I care about, so I have no need to worry about moving the data off, I just want it to be writable!  Thanks for the help!

---

### Post by oldfred on 2013-07-14
If there is no data, you should just be able to repartition & reformat. 
Otherwise you may have to run gdisk repairs to correct partition table and then run fsck to repair file system.

 repair gpt:
[http://www.rodsbooks.com/gdisk/repairing.html](http://www.rodsbooks.com/gdisk/repairing.html)

      If separate drive and unmounted you do not need liveCD.
 #From liveCD so everything is unmounted,swap off if necessary, change example shown with partition sdb1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sdb1
#if errors: -y auto answers yes for fixes needing response, also see man e2fsck
sudo e2fsck -f -y -v /dev/sdb1

---

### Post by scambro on 2013-07-14
> **oldfred said:**
> If there is no data, you should just be able to repartition & reformat. 
Otherwise you may have to run gdisk repairs to correct partition table and then run fsck to repair file system.

 repair gpt:
[http://www.rodsbooks.com/gdisk/repairing.html](http://www.rodsbooks.com/gdisk/repairing.html)

      If separate drive and unmounted you do not need liveCD.
 #From liveCD so everything is unmounted,swap off if necessary, change example shown with partition sdb1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sdb1
#if errors: -y auto answers yes for fixes needing response, also see man e2fsck
sudo e2fsck -f -y -v /dev/sdb1

I'm reading through that page, but I'm not sure I'm fully grasping all of it, or I'm missing something.  It's not letting me make a partition, so I can't get to e2fsck yet.  When I run gdisk, all of the options that I do give me some type of error:

View Partitions:
```

Command (? for help): p
Disk /dev/sdd: 5860533168 sectors, 2.7 TiB
Logical sector size: 512 bytes
Disk identifier (GUID): 9B6BD1AD-C183-412F-9EC4-86C5D9992E48
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 5860533134
Partitions will be aligned on 2048-sector boundaries
Total free space is 5860533101 sectors (2.7 TiB)

Number  Start (sector)    End (sector)  Size       Code  Name

Command (? for help): 

```

Create New Partition:
```

Command (? for help): n
Partition number (1-128, default 1): 
First sector (34-5860533134, default = 34) or {+-}size{KMGTP}: 
Information: Moved requested sector from 34 to 2048 in
order to align on 2048-sector boundaries.
Use 'l' on the experts' menu to adjust alignment
Last sector (2048-5860533134, default = 5860533134) or {+-}size{KMGTP}: 
Current type is 'Linux filesystem'
Hex code or GUID (L to show codes, Enter = 8300): 
Changed type of partition to 'Linux filesystem'

Command (? for help): w

Final checks complete. About to write GPT data. THIS WILL OVERWRITE EXISTING
PARTITIONS!!

Do you want to proceed? (Y/N): Y
OK; writing new GUID partition table (GPT).
Unable to save backup partition table! Perhaps the 'e' option on the experts'
menu will resolve this problem.
[b]Warning! An error was reported when writing the partition table! This error
MIGHT be harmless, but you may have trashed the disk![/b]

Command (? for help): 

```

View partition in recovery menu after attempting the above:
```

Command (? for help): r

Recovery/transformation command (? for help): p
Disk /dev/sdd: 5860533168 sectors, 2.7 TiB
Logical sector size: 512 bytes
Disk identifier (GUID): 9B6BD1AD-C183-412F-9EC4-86C5D9992E48
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 5860533134
Partitions will be aligned on 2048-sector boundaries
Total free space is 2014 sectors (1007.0 KiB)

Number  Start (sector)    End (sector)  Size       Code  Name
   1            2048      5860533134   2.7 TiB     8300  Linux filesystem

Recovery/transformation command (? for help): i
Using 1
Partition GUID code: 0FC63DAF-8483-4772-8E79-3D69D8477DE4 (Linux filesystem)
Partition unique GUID: 14048A7E-A2FB-4340-A81F-987BB1C55BEE
First sector: 2048 (at 1024.0 KiB)
Last sector: 5860533134 (at 2.7 TiB)
Partition size: 5860531087 sectors (2.7 TiB)
Attribute flags: 0000000000000000
Partition name: 'Linux filesystem'

Recovery/transformation command (? for help): 

```

---

### Post by oldfred on 2013-07-14
I have not seen that type of issue. It seems to have issues with backup partition table.

Have you tried the e for experts?
How was NAS formatted/partitioned? Perhaps some sort of RAID that is interfering?
Some have use XFS formatting which then requires different formatting, but partitioning should be the same.

---

### Post by scambro on 2013-07-14
> **oldfred said:**
> I have not seen that type of issue. It seems to have issues with backup partition table.

Have you tried the e for experts?
How was NAS formatted/partitioned? Perhaps some sort of RAID that is interfering?
Some have use XFS formatting which then requires different formatting, but partitioning should be the same.

The outcome appears to be the same...  

create a new protective MBR:
```

Expert command (? for help): n

```

print protective MBR data
```

Expert command (? for help): o

Disk size is 5860533168 sectors (2.7 TiB)
MBR disk identifier: 0x00000000
MBR partitions:

Number  Boot  Start Sector   End Sector   Status      Code
   1                     1   4294967295   primary     0xEE

```

write table to disk and exit
```

Expert command (? for help): w

Final checks complete. About to write GPT data. THIS WILL OVERWRITE EXISTING
PARTITIONS!!

Do you want to proceed? (Y/N): Y
OK; writing new GUID partition table (GPT).
Unable to save backup partition table! Perhaps the 'e' option on the experts'
menu will resolve this problem.
Warning! An error was reported when writing the partition table! This error
MIGHT be harmless, but you may have trashed the disk!

```

verify disk
```

Expert command (? for help): v

No problems found. 5860533101 free sectors (2.7 TiB) available in 1
segments, the largest of which is 5860533101 (2.7 TiB) in size.

Expert command (? for help): 

```

---

### Post by scambro on 2013-07-14
Oh, it was in a Netgear ReadyNAS, running as an X-RAID system.  I've taken two other drives from the NAS and removed the partitions, then the NAS read them just fine.  This one (which was the one in the NAS when the power was interrupted) is giving me fits.

---

### Post by oldfred on 2013-07-14
RAID drives keep meta-data on drive. Usually that interferes with the install of grub if converting back to non-RAID.

I might try this if drive is not still RAID. Run just on drive that you are working on.

Presence1960 on remove old raid setting from HD
[http://ubuntuforums.org/showthread.php?t=1325650](http://ubuntuforums.org/showthread.php?t=1325650)
sudo dmraid -E -r /dev/sda
sudo dmraid -E -r /dev/sdb
Also check BIOS for raid settings
More discussion:
[http://wwww.ubuntuforums.org/showthread.php?p=9274738#post9274738](http://wwww.ubuntuforums.org/showthread.php?p=9274738#post9274738)

---

### Post by scambro on 2013-07-14
I'm still reading through some of the information in those threads, but I don't think the RAID piece is the issue.  I did see a RAID partition on one of the other two drives that is working, but I simply deleted it in parted without an issue.  When I ran that command on this drive, I still get lots of input/ output errors:

```

:~$ sudo dmraid -E -r /dev/sdd
ERROR: asr: reading /dev/sdd[Input/output error]
ERROR: ddf1: reading /dev/sdd[Input/output error]
ERROR: ddf1: reading /dev/sdd[Input/output error]
ERROR: hpt37x: reading /dev/sdd[Input/output error]
ERROR: hpt45x: reading /dev/sdd[Input/output error]
ERROR: isw: reading /dev/sdd[Input/output error]
ERROR: isw: reading /dev/sdd[Input/output error]
ERROR: isw: reading /dev/sdd[Input/output error]
ERROR: jmicron: reading /dev/sdd[Input/output error]
ERROR: lsi: reading /dev/sdd[Input/output error]
ERROR: nvidia: reading /dev/sdd[Input/output error]
ERROR: pdc: reading /dev/sdd[Input/output error]
ERROR: pdc: reading /dev/sdd[Input/output error]
ERROR: pdc: reading /dev/sdd[Input/output error]
ERROR: pdc: reading /dev/sdd[Input/output error]
ERROR: sil: reading /dev/sdd[Input/output error]
ERROR: via: reading /dev/sdd[Input/output error]
no raid disks and with names: "/dev/sdd"

```

And thanks for all the assistance!

---

### Post by oldfred on 2013-07-14
All those errors are it just tying every type of RAID. It looks like it did not find any to remove as you suspected.

Not sure why then gdisk will not write backup partition table.
I might try gparted.
       Under device, create partition table, advanced, choose gpt not the default msdos (MBR) partitioning.

---

### Post by scambro on 2013-07-14
> **oldfred said:**
> All those errors are it just tying every type of RAID. It looks like it did not find any to remove as you suspected.

Not sure why then gdisk will not write backup partition table.
I might try gparted.
       Under device, create partition table, advanced, choose gpt not the default msdos (MBR) partitioning.

That also gave me a bunch of input/ output errors.  I found a few other threads online about destroyed MBRs and manually rebuilding them, but nothing about the steps to how to do that.  That's not anything I've gotten my hands into before.  For instance:

[http://superuser.com/questions/481196/cannot-access-disk-partition-table-broken](http://superuser.com/questions/481196/cannot-access-disk-partition-table-broken)

That's almost identical to what I did, however, I see no signs that I have badsectors.  I've been running badblocks for an hour and have 0 errors still.

---

### Post by oldfred on 2013-07-14
I do not think issue is MBR, as the gpt only has a protective MBR so old partition tools like fdisk do not attempt to repartition a gpt drive.
Something to do with backup gpt table which gdisk wants to write near end of drive. Or as if end of drive is damaged?

---

