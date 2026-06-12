---
title: "Ubuntu DVD Startup 'Fixes' Partition table - Wrongly assumes RAID - Corrupts parts"
date: 2014-06-26
forum: General Help
---

### Post by calmcoder77 on 2014-06-26
[FONT=arial][SIZE=2][COLOR=#333333]Testdisk deep search is unable to detect the correct partition table for /dev/sdb, after starting the PC from DVD (Ubuntu 14.04 LTC *Trusty Tahr* - Release amd64 (20140417)), and experiencing the following invasive action right at the beginning of the DVD startup:
[/COLOR]```
Unable to open '/dev/dm-0'
The disk contains an unclean file system (0, 0).
The file system wasn't safely closed on Windows. Fixing.
The disk contains an unclean file system (0, 0).
The file system wasn't safely closed on Windows. Fixing.
The disk contains an unclean file system (0, 0).
The file system wasn't safely closed on Windows. Fixing.

Unable to open '/dev/sdb'
The disk contains an unclean file system (0, 0).
The file system wasn't safely closed on Windows. Fixing.

Unable to open '/dev/sdd'
/init: line 7: can't open ?????? (my edit: maybe /dev/sr0): No medium found
Generating locales...
```


[COLOR=#333333]My guess is that /dev/dm-0 refers to /dev/sdc, because it was the only drive to have 3 partitions at that point, and there are 3 file system fixes listed for this drive. /dev/dm-0 (shown as /dev/sdc by Testdisk) is also a designation for part of a RAID volume, of which /dev/sdb is the second drive in what Ubuntu (wrongly) thought is an active RAID array.[/COLOR]
[COLOR=#333333]
This /dev/dm-0 designation is a wrong carry-over from a botched Intel Rapid Storage Driver installation that happened when Windows was installed the first time, this Intel Driver tried to pair 2x 1.5 TB drives (/dev/sdc & /dev/sdb) together in a RAID array without warning. Windows was promptly reinstalled without this Intel Driver and the partition table of /dev/sdb was recovered after the install with Testdisk, this was more than a year ago.[/COLOR]
[COLOR=#333333]The PC worked fine since then with Windows 7, until I tried to start an Ubuntu DVD simply to Try Ubuntu today. How unfortunate that it would overwrite partition tables and filenames right at startup, without even a hint of a prompt or agreement from my side.
[/COLOR]
[COLOR=#333333]The current drive configuration in the PC is as follows:[/COLOR]
```
Disk /dev/sda - 1500 GB / 1397 GiB - Samsung HD154UI
Disk /dev/sdb - 1500 GB / 1397 GiB - ST31500341AS
Disk /dev/sdc - 1500 GB / 1397 GiB - ST31500341AS
Disk /dev/sdd - 200 GB / 186 GiB - ST3200826AS

/dev/sda:   [1397.26 GiB NTFS (Healthy, Primary)]
/dev/sdb:   should be [1251 GB NTFS] [249 GB NTFS], but currently is offline [774.57 GiB][390.63 GiB][232.07 GiB]
/dev/sdc:   [774.57 GiB NTFS (Healthy, Primary, Active)] [390.63 GiB NTFS Healthy, Primary] [232.07 GiB Unallocated]
/dev/sdd:   [100 MiB NTFS (Healthy, System, Primary, Active)] [186.21 GiB NTFS (Healthy, Boot, Primary)]

```

[COLOR=#333333]The approximately correct partition table of /dev/sdb, the drive I want to recover, is as follows, although I'm not 100% sure:[/COLOR]
```
Disk /dev/sdb - 1500 GB / 1397 GiB - CHS 182401 255 63
Partition       Start           End         Size in sectors
1 * HPFS - NTFS 0 32 33         152106 139 33   2443599146  [Piet]  (1251 GB)
2 P HPFS - NTFS 152107    0   1     182400 254 63     486673110     [Files]     (249 GB)

```

[COLOR=#333333]It could also maybe be, although in that case partition #2 was never seen or used, and I only want to recover partition #1 and #3.[/COLOR]
```
Disk /dev/sdb - 1500 GB / 1397 GiB - CHS 182401 255 63
Partition       Start           End         Size in sectors
1 * HPFS - NTFS 0 32 33         x x x   1956926036  [Piet]  (1002 GB)
2 P HPFS - NTFS x   x   x   152106 139 33     486673110     [?]     (249 GB)
3 P HPFS - NTFS 152107    0   1     182400 254 63     486673110     [Files]     (249 GB)

```

[COLOR=#333333]A Testdisk Quick Search reveals the following partition table for /dev/sdb:[/COLOR]
```
Disk /dev/sdb - 1500 GB / 1397 GiB - CHS 182401 255 63
Partition       Start           End         Size in sectors
1 * HPFS - NTFS 0 32 33         10113 179 58    1624389632  [Francois Files]    (831 GB)
2 P HPFS - NTFS 101113 179 59   152106 139 33     819200000                     (419 GB)
3 P HPFS - NTFS 152107    0   1     182400 254 63     486673110     [Files]     (249 GB)

(NTFS, blocksize=4096, 831 GB / 774 GiB)
(NTFS, blocksize=4096, 419 GB / 390 GiB)
(NTFS, blocksize=4096, 249 GB / 232 GiB)
```
[COLOR=#333333]
After Testdisk Deep Search the following is displayed for /dev/sdb:[/COLOR]
```
Disk /dev/sdb - 1500GB / 1397 GiB - CHS 182401 255 63

The harddisk <1500 GB / 1397 GiB> seems too small! << 1749 GB / 1629 GiB>
Check the harddisk size: HD jumpers settings, BIOS detection...

The following partitions can't be recovered:
Partition       Start           End         Size in sectors
FAT16 LBA       155655 200 54   186533 126 25   496050380       (253 GB)
HPFS - NTFS 182400 254 63   212694 254 62   486673110

```

[COLOR=#333333]After pressing [Enter] the following Deep Search result for /dev/sdb is shown, but it is wrong.[/COLOR]
```
Disk /dev/sdb - 1500 GB / 1397 GiB - CHS 182401 255 63
Partition       Start           End         Size in sectors
HPFS - NTFS 0 32 33         10113 179 58    1624389632  [Francois Files]    (831 GB)
HPFS - NTFS 0 32 33         182401 35 34    2930272256  [Francois Files]    (1500 GB)
HPFS - NTFS 101113 179 59   152106 139 33     819200000                     (419 GB)
HPFS - NTFS 152107    0   1     182400 254 63     486673110     [Files]     (249 GB)

    (NTFS, blocksize=4096, 831 GB / 774 GiB)
    (NTFS found using backup sector, blocksize=4096, 1500GB / 1397 GiB)
    (NTFS, blocksize=4096, 419 GB / 390 GiB)
    (NTFS, blocksize=4096, 249 GB / 232 GiB)

```[COLOR=#333333]

When [P] is pressed for each listed partition, the files that are shown for partition #1 [Francois Files], and partition #3 [419 GB] are exactly the files that are on the two partitions as they appear on the other 1.5TB drive /dev/sdc, so the filenames and foldernames were also copied from /dev/sdc to /dev/sdb by the Ubuntu DVD, like the partition table, which was completely invasive and undesired.
[/COLOR]
[COLOR=#333333]Partition #2 [Francois Files] (1500 GB) cannot find a valid file system, and Partition #4 [Files] actually shows the correct files for the correct partition, so now only the first correct partition must be recovered.[/COLOR]
[COLOR=#333333]Please take note of the partition table of the other 1.5TB drive, /dev/sdc, and notice how the Ubuntu DVD copied this partition table of /dev/sdc to /dev/sdb. But, not only was the partition table copied to /dev/sdb, but also the file names and folders (MFT?).
[/COLOR]
```
Disk /dev/sdc - 1500 GB / 1397 GiB - CHS 182401 255 63
Partition       Start           End         Size in sectors
1 * HPFS - NTFS 0 32 33         10113 179 58    1624389632  [Francois Files]    (831 GB)
2 P HPFS - NTFS 101113 179 59   152106 139 33     819200000                     (419 GB)

    (NTFS, blocksize=4096, 831 GB / 774 GiB)
    (NTFS, blocksize=4096, 419 GB / 390 GiB)

```

[COLOR=#333333]I am desperate to recover the exact partition table of /dev/sdb, in particular the first partition as it was before I started the Ubuntu DVD, which was a truly regrettable action of which I never would've imagined it would do something so invasive without even a prompt, right at the startup. Luckily I had the presence of mind to take a photo with my cellphone when I saw the 'fixing' messages as the DVD booted up.[/COLOR]
[COLOR=#333333]Is it possible to try something more than the Testdisk Deep Search to try and recover the partition table?[/COLOR]
[COLOR=#333333]
This problem very much pertains to how Ubuntu tried to fix a partition table, under the wrong assumptions due to an incorrect disk designation. Maybe we can get an answer as to the exact process or program that was used in the Ubuntu DVD startup that fixes disk issues.

Testdisk.log: [https://drive.google.com/file/d/0BwlNU8avxOwRVGFmbncySVdNUFk/edit?usp=sharing](https://drive.google.com/file/d/0BwlNU8avxOwRVGFmbncySVdNUFk/edit?usp=sharing)

Screenshots: [https://drive.google.com/folderview?id=0BwlNU8avxOwRSDdTSHRMWjNTVjQ&usp=sharing](https://drive.google.com/folderview?id=0BwlNU8avxOwRSDdTSHRMWjNTVjQ&usp=sharing)

Did Ubuntu DVD make this an active RAID array, somehow, or did it just replicate the first 1.5TB partition to the second? I felt like it spent only a couple of seconds doing the 'fixing', not really enough time to RAID 0 or RAID 1 the actual files. But why are the filenames also present on the second 1.5TB of the supposed RAID array?

Please, desperately need some help here, or at least a pointing in the right direction.[/COLOR][/SIZE][/FONT]

---

### Post by grahammechanical on 2014-06-26
You are making inaccurate claims about the Ubuntu Live Session DVD image. It does not do what you say it has done.

The live session does not change partition tables or create RAID. But when we install Ubuntu, then we can instruct the installer to do things like that. I have run plenty of Ubuntu live sessions and I have done plenty of Ubuntu installs of Ubuntu and its flavours all during their development period and I know what the live session is able to do and what it cannot do without authorization.

---

### Post by calmcoder77 on 2014-06-26
Hi, thanks for the reply.

This was just the normal latest Ubuntu DVD, I'm not sure if there is a special Ubuntu Live Session DVD.

However, in using the normal latest Ubuntu DVD [COLOR=#333333][FONT=arial](Ubuntu 14.04 LTC [/FONT][/COLOR]*Trusty Tahr - Release amd64 (20140417))* right
at the first text shown on the screen from starting the DVD, we have 

```
Unable to open '/dev/dm-0'
The disk contains an unclean file system (0, 0).
The file system wasn't safely closed on Windows. Fixing.
The disk contains an unclean file system (0, 0).
The file system wasn't safely closed on Windows. Fixing.
The disk contains an unclean file system (0, 0).
The file system wasn't safely closed on Windows. Fixing.

Unable to open '/dev/sdb'
The disk contains an unclean file system (0, 0).
The file system wasn't safely closed on Windows. Fixing.

Unable to open '/dev/sdd'
/init: line 7: can't open ?????? (my edit: maybe /dev/sr0): No medium found
Generating locales...
```

If the special Live Session DVD behaves differently then you are probably correct, but it was still
a shock to see that the normal installation DVD would do this sort of invasive thing right at the
startup, before any prompt was even given to Try Ubuntu or Install Ubuntu. Way before, right
at the startup, it 'fixed' disk partition tables.

I never would've expected this, and never had this trouble with a Linux DVD/CD before.

I'm trying to find out if Ubuntu actually made an active Raid array during this <10 sec 'fixing' period,
or if it just blindly copied the partition table and MFT in this short time, whilst the disks are still separate?

Windows took the second drive (/dev/sdb) offline, because it says that its signature clashes with /dev/sdc.

Please, any advice on how I can safely recover my files from the second disk /dev/sdb.

Can I safely make an image of the second disk, without Windows trying to correct something on what it might
perceive as a broken Raid array? What would be the best program to safely make an image?

I'd appreciate any help.

---

