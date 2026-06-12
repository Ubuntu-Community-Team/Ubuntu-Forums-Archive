---
title: "Fix Win7 MBR from Ubuntu"
date: 2015-08-20
forum: General Help
---

### Post by dfresh41302 on 2015-08-20
Ok, so I have my system dual booting Ubuntu 12.04/Win7 from the same hard drive for years with no issues.  The Win7 instance starts giving the unmountable boot volume error now and Ubuntu is fine.  Looks like I just need to run chkdsk, but not as easy it sounds.  Booting to Win7 install CD from USB works, but it can't detect the C drive to repair anything.  It seems my only option is to use Ubuntu to fix it somehow.  In searching it seems I can use some tools to fix it, but all the examples given seem to show users who have Ubuntu and Windows on separate disks.  Below is the output from fdisk.  sda1 is where my Win7 OS partition exists.  Can anyone provide any suggestions on what I should try?

```

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x4a1d4a1c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      206847      102400    7  HPFS/NTFS/exFAT
/dev/sda2          206848   838862847   419328000    7  HPFS/NTFS/exFAT
/dev/sda3       838864894   976771071    68953089    5  Extended
/dev/sda5       838864896   968386559    64760832   83  Linux
/dev/sda6       968388608   976771071     4191232   82  Linux swap / Solaris

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00011a9f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1           16065   976768064   488376000    f  W95 Ext'd (LBA)
/dev/sdb5           16128   976768064   488375968+   7  HPFS/NTFS/exFAT

Disk /dev/sdc: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0009bc79

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1            2048  3907028991  1953513472   83  Linux

```

---

### Post by yancek on 2015-08-20
You could check the link below which has a few possibilities including using the boot repair disk.  The normal and suggested way is to use your windows installation medium and select the repair option.  Using this is also explained at the link below.  If that doesn't work, you have some serious problems.  Also, sda1 is not your windows system partition but rather the boot partition and is marked as such in the output you posted.  The system is on sda2 although boot files are on sda1.

---

### Post by dfresh41302 on 2015-08-21
Did the link make it through on your reply?

---

### Post by yancek on 2015-08-21
Sorry, forgot to post the link and can't find it now.  You might try ntfsfix which has limited capabilities and might not work.  You need ntfs-3g installed and I think also ntfsprogs, not sure about the latter.  Also, have you tried boot repair?  Might download that and give it a try from Ubuntu.  I would not expect much luck if you can't get your windows install medium to detect that partition from the repair option.  Good luck.

---

### Post by oldfred on 2015-08-21
Windows is very particular about the PBR or partition boot sector. That is like a MBR in structure and is first sector of every partition. But with NTFS partitions it must have the NTFS signature and same start & size of partition as MBR's partition table. If not correct Windows will not even see the NTFS partition even though partition table says it is NTFS.

You normally use chkdsk to also repair a NTFS PBR, but if not seen then you may need to totally rebuild it or restore from backup. Then chkdsk should work.

First run the Summary report from Boot-Repair as it will show if partition boot sector is seen as NTFS. Or may show other issues.

       Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

