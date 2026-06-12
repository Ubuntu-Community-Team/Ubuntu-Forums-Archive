---
title: "Disks says 500GB Seagate drive is OK, one bad sector. No edit options."
date: 2017-12-20
forum: General Help
---

### Post by soundgeek on 2017-12-20
The 500GB Seagate drive ran Win7, but now won't boot. I've installed a new 2TB drive with Win7 & Ubuntu on it. Win7 does not see the 500GB drive. Ubuntu Disks utility says "One bad sector", but does not offer any edit/fix options, only Edit Mount Options.

It there any way I might get the 500GB drive to mount? I'd like to rescue a few files if I can.

---

### Post by Autodave on 2017-12-20
Probably not: sounds like the boot sector is the bad sector.

There are places online that offer data rescue from dead discs, but this is expensive and there is no guarantee of getting anything in return.

---

### Post by soundgeek on 2017-12-20
> **Autodave said:**
> Probably not: sounds like the boot sector is the bad sector.

There are places online that offer data rescue from dead discs, but this is expensive and there is no guarantee of getting anything in return.

Yes it does sound like the boot sector is the bad sector. Is there no way of re-mapping it somewhere else & creating a new one?

---

### Post by dragonfly41 on 2017-12-20
You could clone the disk image to a new drive and then try testdisk to recover cloned data.

[https://www.cgsecurity.org/wiki/Damaged_Hard_Disk](https://www.cgsecurity.org/wiki/Damaged_Hard_Disk)

Testdisk can run in a LiveUSB.

---

### Post by yancek on 2017-12-20
> Ubuntu Disks utility says "One bad sector", but does not offer any edit/fix options, only Edit Mount Options.

What happens when you select the Mount option?

When you run:  sudo fdisk -l (Lower Case Letter L in command) does the second drive show?  You should be able to tell which drive is which becasue the size of each drive will show in the output.  Since the partitions are windows, you might try running ntfsfix on each partition consecutively.  Might fix a very minor problem.  If you just installed windows 7 you have the windows install disk so you might try booting that and selecting the Repair option and running the chkdsk command.

---

### Post by soundgeek on 2017-12-20
> **dragonfly41 said:**
> You could clone the disk image to a new drive and then try testdisk to recover cloned data.

[https://www.cgsecurity.org/wiki/Damaged_Hard_Disk](https://www.cgsecurity.org/wiki/Damaged_Hard_Disk)

Testdisk can run in a LiveUSB.

I hadn't thought of that. I have a spare disk of the same size so I might try that. Perhaps I could use clonezilla? I''ll read through your linked info. Thanks for the suggestion.

---

### Post by soundgeek on 2018-01-01
Thanks for responding yancek. Although the 'disk's utility lists the faulty drive, no options are offered except Edit Mount Options. No mount option is offered.

Windows doesn't see the faulty drive.

I tried fdisk -l. I got:
```

Device     Boot      Start        End    Sectors   Size Id Type
/dev/sda1  *            63    4096574    4096512     2G  6 FAT16
/dev/sda2          4096636 3907028991 3902932356   1.8T  f W95 Ext'd (LBA)
/dev/sda5          4096638 1955544254 1951447617 930.5G  7 HPFS/NTFS/exFAT
/dev/sda6       1955545088 1986793471   31248384  14.9G 82 Linux swap / Solaris
/dev/sda7       1986795520 2049294335   62498816  29.8G 83 Linux
/dev/sda8       2049296384 3907028991 1857732608 885.9G 83 Linux

Partition 1 does not start on physical sector boundary.
Partition 2 does not start on physical sector boundary.
Partition 5 does not start on physical sector boundary.


Disk /dev/sdc: 15.1 GiB, 16170196480 bytes, 31582415 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x04dd5721

Device     Boot Start      End  Sectors  Size Id Type
/dev/sdc1  *       63 31567724 31567662 15.1G  c W95 FAT32 (LBA)

```

Happy new year!

---

### Post by rbmorse on 2018-01-02
Clonezilla will clone the bad sector...the resulting copy will not work any better than the original. The reason for the clone is so you won't have to run Testdisk, or other disk repair utility, against the original drive. That way, if there's a problem or you make a mistake (possible...testdisk's UI is a bit obtuse in places) just erase the drive with the clone copy, make a new clone of the original disk and start over on the new copy. 

Making a clone of the original and using Testdisk or other recovery utilities only on the clone copy is critical. Don't ask me how I know this.

---

### Post by soundgeek on 2018-01-04
Thank you rbmorse. I'm guessing this is hard-won knowledge!

---

### Post by soundgeek on 2018-01-20
> **dragonfly41 said:**
> You could clone the disk image to a new drive and then try testdisk to recover cloned data.

[https://www.cgsecurity.org/wiki/Damaged_Hard_Disk](https://www.cgsecurity.org/wiki/Damaged_Hard_Disk)

Testdisk can run in a LiveUSB.

I've dowloaded Knoppix 8.1 onto DVD & it boots fine. But really I need a drive on USB as I only have two serial interfaces for HDDs. I suppose one option is to have the target drive in a USB caddy?

The other option seems to be running Testdisk in a LiveUSB. I don't know what this is really. Is is it a bootable knoppix system on a USB drive? I have a portable USB DVD drive. Would that do?

---

### Post by soundgeek on 2018-01-27
> **dragonfly41 said:**
> You could clone the disk image to a new drive and then try testdisk to recover cloned data.  [https://www.cgsecurity.org/wiki/Damaged_Hard_Disk](https://www.cgsecurity.org/wiki/Damaged_Hard_Disk)  Testdisk can run in a LiveUSB.  I tried ddrescue. It didn't seem to do anything. Am I getting this wrong?  ```
 knoppix@Microknoppix:~/ddrescue-1.9$ ./ddrescue -n /dev/sda /dev/sdb rescued.log   Press Ctrl-C to interrupt Initial status (read from logfile) rescued:         0 B,  errsize:       0 B,  errors:       0 Current status rescued:         0 B,  errsize:       0 B,  current rate:        0 B/s    ipos:         0 B,   errors:       0,    average rate:        0 B/s    opos:         0 B Finished        knoppix@Microknoppix:~/ddrescue-1.9$ ./ddrescue -r 1 /dev/sda /dev/sdb rescued.log   Press Ctrl-C to interrupt Initial status (read from logfile) rescued:         0 B,  errsize:       0 B,  errors:       0 Current status rescued:         0 B,  errsize:       0 B,  current rate:        0 B/s    ipos:         0 B,   errors:       0,    average rate:        0 B/s    opos:         0 B Finished 
```

---

