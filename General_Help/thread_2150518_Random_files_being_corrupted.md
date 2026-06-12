---
title: "Random files being corrupted"
date: 2013-06-01
forum: General Help
---

### Post by Pedlar88 on 2013-06-01
[COLOR=#000000][FONT=HPRegular]Hello,[/FONT][/COLOR]

[COLOR=#000000][FONT=HPRegular]I have a DL380 G4 with 4gb Ram, and 6 146gb Seagate Cheetah 10k Drives in a RAID 5 configuration using the Integrated Smart Array 6i Controller, and am using Ubuntu 12.04 (x86_64) OS.[/FONT][/COLOR]

[COLOR=#000000][FONT=HPRegular]I've been having issues with this setup for the past week or so, getting EXT4-fs errors, so I switched to EXT3-fs, and still receiving the same errors.[/FONT][/COLOR]

[COLOR=#000000][FONT=HPRegular]The latest one on EXT3 was:[/FONT][/COLOR]
[COLOR=#000000][FONT=HPRegular][ 10.644162] EXT3-fs error (device dm-0): ext3_add_entry: bad entry in directory #3162531: rec_len % 4 != 0 - offset=48, inode=1774361275, rec_len=28257, name_len=45
[ 10.658877] Aborting journal on device dm-0.
[ 10.664328] EXT3-fs (dm-0): error: remounting filesystem read-only

I then reinstalled EXT4 and got:
[/FONT][/COLOR][60050.894870] EXT4-fs error (device dm-0): htree_dirblock_to_tree:861: inode #9970869: block 39854723: comm git: bad entry in directory: rec_len is smaller than minimal - offset=0(0), inode=0, rec_len=0, name_len=0
[60050.922190] Aborting journal on device dm-0-8.
[60050.931515] EXT4-fs (dm-0): Remounting filesystem read-only

So looked up the inum with find, and it was the directory I was trying to cd into.


pedlar@server:~/cm/external/llvm$ find . -inum 9970869
./include/llvm/MC

pedlar@server:~/cm/external/llvm$ df -h
Filesystem               Size  Used Avail Use% Mounted on
/dev/mapper/server-root  669G   18G  617G   3% /
udev                     1.9G  4.0K  1.9G   1% /dev
tmpfs                    778M  272K  778M   1% /run
none                     5.0M     0  5.0M   0% /run/lock
none                     1.9G     0  1.9G   0% /run/shm
/dev/cciss/c0d0p1        228M   27M  190M  13% /boot


[COLOR=#000000][FONT=HPRegular]
But I've also been getting a lot of segfault errors, that go away when I reboot, and come back eventually.[/FONT][/COLOR]

[COLOR=#000000][FONT=HPRegular]So in thinking it was a Hardware issue I did S.M.A.R.T tests on all of my drives (both long, and short) and all of them passed both tests. I've also ran memtest86 for about 3-4 passes through and all of those passed as well.[/FONT][/COLOR]

[COLOR=#000000][FONT=HPRegular]I'm wondering if anyone here has any more Diagnostic Check ideas I can run to narrow down this issue even more, as I've started to run out of ideas.[/FONT][/COLOR]

[COLOR=#000000][FONT=HPRegular]Another Interesting thing is when I create the Array in ACU through SmartStart it shows the logical drive as Max 683.6gb. but when Installing any OS, the Drive volume is 740gb.[/FONT][/COLOR]


[COLOR=#000000][FONT=HPRegular]Smartctl results:[/FONT][/COLOR]
```

[COLOR=#000000][FONT=HPRegular]root@server:~# for i in {0..5}; do echo "Drive $i"; smartctl -a -d cciss,$i /dev/cciss/c0d0; echo ""; done | less[/FONT][/COLOR][COLOR=#000000][FONT=HPRegular]
Drive 0
smartctl 5.41 2011-06-09 r3365 [x86_64-linux-3.5.0-23-generic] (local build)
Copyright (C) 2002-11 by Bruce Allen, [http://smartmontools.sourceforge.net]("http://smartmontools.sourceforge.net/")[/FONT][/COLOR]
[COLOR=#000000][FONT=HPRegular]Vendor: FUJITSU
Product: MAP3147NC
Revision: 5608
User Capacity: 146,815,733,760 bytes [146 GB]
Logical block size: 512 bytes
Serial number: UQ07P4A04LEP
Device type: disk
Transport protocol: Parallel SCSI (SPI-4)
Local Time is: Fri May 31 11:17:03 2013 CDT
Device supports SMART and is Enabled
Temperature Warning Disabled or Not Supported
SMART Health Status: OK[/FONT][/COLOR]
[COLOR=#000000][FONT=HPRegular]Current Drive Temperature: 33 C
Drive Trip Temperature: 65 C
Manufactured in week 43 of year 2004
Specified cycle count over device lifetime: 10000
Accumulated start-stop cycles: 74
Elements in grown defect list: 0[/FONT][/COLOR]
[COLOR=#000000][FONT=HPRegular]Error counter log:
Errors Corrected by Total Correction Gigabytes Total
ECC rereads/ errors algorithm processed uncorrected
fast | delayed rewrites corrected invocations [10^9 bytes] errors
read: 0 21 0 0 0 43065.555 0
write: 0 1 0 0 0 7240.451 0
verify: 0 0 0 0 0 4902.749 0[/FONT][/COLOR]
[COLOR=#000000][FONT=HPRegular]Non-medium error count: 389[/FONT][/COLOR]
[COLOR=#000000][FONT=HPRegular]SMART Self-test log
Num Test Status segment LifeTime LBA_first_err [SK ASC ASQ]
Description number (hours)
# 1 Background short Completed - 27076 - [- - -]
# 2 Background long Completed - 27055 - [- - -]
# 3 Background long Completed - 26927 - [- - -]
# 4 Background short Completed - 26925 - [- - -]
# 5 Background short Completed - 26866 - [- - -]
# 6 Background long Completed - 1 - [- - -][/FONT][/COLOR]
[COLOR=#000000][FONT=HPRegular]Long (extended) Self Test duration: 2621 seconds [43.7 minutes][/FONT][/COLOR]


[COLOR=#000000][FONT=HPRegular]Drive 1
smartctl 5.41 2011-06-09 r3365 [x86_64-linux-3.5.0-23-generic] (local build)
Copyright (C) 2002-11 by Bruce Allen, [http://smartmontools.sourceforge.net]("http://smartmontools.sourceforge.net/")[/FONT][/COLOR]
[COLOR=#000000][FONT=HPRegular]Vendor: SEAGATE
Product: ST3146707LC
Revision: D701
User Capacity: 146,815,733,760 bytes [146 GB]
Logical block size: 512 bytes
Serial number: 3KS1L65Y
Device type: disk
Transport protocol: Parallel SCSI (SPI-4)
Local Time is: Fri May 31 11:17:04 2013 CDT
Device supports SMART and is Enabled
Temperature Warning Enabled
SMART Health Status: OK[/FONT][/COLOR]
[COLOR=#000000][FONT=HPRegular]Current Drive Temperature: 35 C
Drive Trip Temperature: 68 C
Elements in grown defect list: 0
Vendor (Seagate) cache information
Blocks sent to initiator = 1454822628
Blocks received from initiator = 1223409221
Blocks read from cache and sent to initiator = 3338647048
Number of read and write commands whose size <= segment size = 240360360
Number of read and write commands whose size > segment size = 0
Vendor (Seagate/Hitachi) factory information
number of hours powered up = 54537.98
number of minutes until next internal SMART test = 116[/FONT][/COLOR]
[COLOR=#000000][FONT=HPRegular]Error counter log:
Errors Corrected by Total Correction Gigabytes Total
ECC rereads/ errors algorithm processed uncorrected
fast | delayed rewrites corrected invocations [10^9 bytes] errors
read: 5439890 0 0 5439890 5439890 13456.683 0
write: 0 0 0 0 0 1475.446 0
verify: 476108967 0 0 476108967 476108967 1620106.637 0[/FONT][/COLOR]
[COLOR=#000000][FONT=HPRegular]Non-medium error count: 12010[/FONT][/COLOR]
[COLOR=#000000][FONT=HPRegular]SMART Self-test log
Num Test Status segment LifeTime LBA_first_err [SK ASC ASQ]
Description number (hours)
# 1 Background short Completed - 54499 - [- - -]
# 2 Background long Completed - 54478 - [- - -]
# 3 Background long Completed - 54456 - [- - -]
# 4 Background short Completed - 54398 - [- - -]
# 5 Background long Completed - 1 - [- - -]
# 6 Background short Completed - 0 - [- - -][/FONT][/COLOR]
[COLOR=#000000][FONT=HPRegular]Long (extended) Self Test duration: 2726 seconds [45.4 minutes][/FONT][/COLOR]



[COLOR=#000000][FONT=HPRegular]Drive 2
smartctl 5.41 2011-06-09 r3365 [x86_64-linux-3.5.0-23-generic] (local build)
Copyright (C) 2002-11 by Bruce Allen, [http://smartmontools.sourceforge.net]("http://smartmontools.sourceforge.net/")[/FONT][/COLOR]
[COLOR=#000000][FONT=HPRegular]Vendor: SEAGATE
Product: ST3146807LC
Revision: DS09
User Capacity: 146,815,733,760 bytes [146 GB]
Logical block size: 512 bytes
Serial number: 3HY9RP06
Device type: disk
Transport protocol: Parallel SCSI (SPI-4)
Local Time is: Fri May 31 11:17:05 2013 CDT
Device supports SMART and is Enabled
Temperature Warning Enabled
SMART Health Status: OK[/FONT][/COLOR]
[COLOR=#000000][FONT=HPRegular]Current Drive Temperature: 35 C
Drive Trip Temperature: 68 C
Elements in grown defect list: 0
Vendor (Seagate) cache information
Blocks sent to initiator = 80496220
Blocks received from initiator = 2757574639
Blocks read from cache and sent to initiator = 2711663054
Number of read and write commands whose size <= segment size = 1857921065
Number of read and write commands whose size > segment size = 5794
Vendor (Seagate/Hitachi) factory information
number of hours powered up = 58643.68
number of minutes until next internal SMART test = 116[/FONT][/COLOR]
[COLOR=#000000][FONT=HPRegular]Error counter log:
Errors Corrected by Total Correction Gigabytes Total
ECC rereads/ errors algorithm processed uncorrected
fast | delayed rewrites corrected invocations [10^9 bytes] errors
read: 120844078 0 0 120844078 120844078 400280.082 0
write: 0 0 0 0 0 26180.766 0[/FONT][/COLOR]
[COLOR=#000000][FONT=HPRegular]Non-medium error count: 117823[/FONT][/COLOR]
[COLOR=#000000][FONT=HPRegular][GLTSD (Global Logging Target Save Disable) set. Enable Save with '-S on'][/FONT][/COLOR]
[COLOR=#000000][FONT=HPRegular]SMART Self-test log
Num Test Status segment LifeTime LBA_first_err [SK ASC ASQ]
Description number (hours)
# 1 Background short Completed - 58609 - [- - -]
# 2 Background long Completed - 58588 - [- - -]
# 3 Background long Completed - 58465 - [- - -]
# 4 Background short Completed - 58461 - [- - -]
# 5 Background short Completed - 58437 - [- - -]
# 6 Background short Completed - 58403 - [- - -]
# 7 Background long Completed - 11 - [- - -]
# 8 Background short Completed - 10 - [- - -][/FONT][/COLOR]
[COLOR=#000000][FONT=HPRegular]Long (extended) Self Test duration: 3072 seconds [51.2 minutes][/FONT][/COLOR]


[COLOR=#000000][FONT=HPRegular]Drive 3
smartctl 5.41 2011-06-09 r3365 [x86_64-linux-3.5.0-23-generic] (local build)
Copyright (C) 2002-11 by Bruce Allen, [http://smartmontools.sourceforge.net]("http://smartmontools.sourceforge.net/")[/FONT][/COLOR]
[COLOR=#000000][FONT=HPRegular]Vendor: SEAGATE
Product: ST3146807LC
Revision: DS09
User Capacity: 146,815,733,760 bytes [146 GB]
Logical block size: 512 bytes
Serial number: 3HY9TFFW
Device type: disk
Transport protocol: Parallel SCSI (SPI-4)
Local Time is: Fri May 31 11:17:05 2013 CDT
Device supports SMART and is Enabled
Temperature Warning Disabled or Not Supported
SMART Health Status: OK[/FONT][/COLOR]
[COLOR=#000000][FONT=HPRegular]Current Drive Temperature: 34 C
Drive Trip Temperature: 68 C
Elements in grown defect list: 0
Vendor (Seagate) cache information
Blocks sent to initiator = 1862183402
Blocks received from initiator = 144326800
Blocks read from cache and sent to initiator = 3321322531
Number of read and write commands whose size <= segment size = 294180989
Number of read and write commands whose size > segment size = 5771
Vendor (Seagate/Hitachi) factory information
number of hours powered up = 60764.37
number of minutes until next internal SMART test = 116[/FONT][/COLOR]
[COLOR=#000000][FONT=HPRegular]Error counter log:
Errors Corrected by Total Correction Gigabytes Total
ECC rereads/ errors algorithm processed uncorrected
fast | delayed rewrites corrected invocations [10^9 bytes] errors
read: 21679267 0 0 21679267 21679267 35978.974 0
write: 0 0 0 0 0 3770.736 0
verify: 428907230 0 0 428907230 428907498 859813.569 0[/FONT][/COLOR]
[COLOR=#000000][FONT=HPRegular]Non-medium error count: 187083[/FONT][/COLOR]
[COLOR=#000000][FONT=HPRegular][GLTSD (Global Logging Target Save Disable) set. Enable Save with '-S on'][/FONT][/COLOR]
[COLOR=#000000][FONT=HPRegular]SMART Self-test log
Num Test Status segment LifeTime LBA_first_err [SK ASC ASQ]
Description number (hours)
# 1 Background short Completed - 60729 - [- - -]
# 2 Background long Completed - 60709 - [- - -]
# 3 Background long Completed - 60586 - [- - -]
# 4 Background short Completed - 60582 - [- - -]
# 5 Background short Completed - 60524 - [- - -]
# 6 Background long Completed - 10 - [- - -]
# 7 Background short Completed - 9 - [- - -][/FONT][/COLOR]
[COLOR=#000000][FONT=HPRegular]Long (extended) Self Test duration: 3072 seconds [51.2 minutes][/FONT][/COLOR]


[COLOR=#000000][FONT=HPRegular]Drive 4
smartctl 5.41 2011-06-09 r3365 [x86_64-linux-3.5.0-23-generic] (local build)
Copyright (C) 2002-11 by Bruce Allen, [http://smartmontools.sourceforge.net]("http://smartmontools.sourceforge.net/")[/FONT][/COLOR]
[COLOR=#000000][FONT=HPRegular]Vendor: SEAGATE
Product: ST3146807LC
Revision: DS09
User Capacity: 146,815,733,760 bytes [146 GB]
Logical block size: 512 bytes
Serial number: 3HY9RMXC
Device type: disk
Transport protocol: Parallel SCSI (SPI-4)
Local Time is: Fri May 31 11:17:06 2013 CDT
Device supports SMART and is Enabled
Temperature Warning Enabled
SMART Health Status: OK[/FONT][/COLOR]
[COLOR=#000000][FONT=HPRegular]Current Drive Temperature: 34 C
Drive Trip Temperature: 68 C
Elements in grown defect list: 0
Vendor (Seagate) cache information
Blocks sent to initiator = 229252668
Blocks received from initiator = 3109780939
Blocks read from cache and sent to initiator = 2739697770
Number of read and write commands whose size <= segment size = 1881841609
Number of read and write commands whose size > segment size = 5963
Vendor (Seagate/Hitachi) factory information
number of hours powered up = 58648.93
number of minutes until next internal SMART test = 116[/FONT][/COLOR]
[COLOR=#000000][FONT=HPRegular]Error counter log:
Errors Corrected by Total Correction Gigabytes Total
ECC rereads/ errors algorithm processed uncorrected
fast | delayed rewrites corrected invocations [10^9 bytes] errors
read: 64453726 0 0 64453726 64453726 400782.861 0
write: 0 0 2 2 60 26503.243 0[/FONT][/COLOR]
[COLOR=#000000][FONT=HPRegular]Non-medium error count: 70442[/FONT][/COLOR]
[COLOR=#000000][FONT=HPRegular][GLTSD (Global Logging Target Save Disable) set. Enable Save with '-S on'][/FONT][/COLOR]
[COLOR=#000000][FONT=HPRegular]SMART Self-test log
Num Test Status segment LifeTime LBA_first_err [SK ASC ASQ]
Description number (hours)
# 1 Background long Completed - 58593 - [- - -]
# 2 Background long Completed - 58470 - [- - -]
# 3 Background short Completed - 58441 - [- - -]
# 4 Background long Completed - 11 - [- - -]
# 5 Background short Completed - 10 - [- - -][/FONT][/COLOR]
[COLOR=#000000][FONT=HPRegular]Long (extended) Self Test duration: 3072 seconds [51.2 minutes][/FONT][/COLOR]


[COLOR=#000000][FONT=HPRegular]Drive 5
smartctl 5.41 2011-06-09 r3365 [x86_64-linux-3.5.0-23-generic] (local build)
Copyright (C) 2002-11 by Bruce Allen, [http://smartmontools.sourceforge.net]("http://smartmontools.sourceforge.net/")[/FONT][/COLOR]
[COLOR=#000000][FONT=HPRegular]Vendor: SEAGATE
Product: ST3146807LC
Revision: DS09
User Capacity: 146,815,733,760 bytes [146 GB]
Logical block size: 512 bytes
Serial number: 3HY9QV0L
Device type: disk
Transport protocol: Parallel SCSI (SPI-4)
Local Time is: Fri May 31 11:17:07 2013 CDT
Device supports SMART and is Enabled
Temperature Warning Enabled
SMART Health Status: OK[/FONT][/COLOR]
[COLOR=#000000][FONT=HPRegular]Current Drive Temperature: 34 C
Drive Trip Temperature: 68 C
Elements in grown defect list: 0
Vendor (Seagate) cache information
Blocks sent to initiator = 84690809
Blocks received from initiator = 2885140073
Blocks read from cache and sent to initiator = 2700374170
Number of read and write commands whose size <= segment size = 1865990889
Number of read and write commands whose size > segment size = 6920
Vendor (Seagate/Hitachi) factory information
number of hours powered up = 58644.02
number of minutes until next internal SMART test = 116[/FONT][/COLOR]
[COLOR=#000000][FONT=HPRegular]Error counter log:
Errors Corrected by Total Correction Gigabytes Total
ECC rereads/ errors algorithm processed uncorrected
fast | delayed rewrites corrected invocations [10^9 bytes] errors
read: 99023039 0 0 99023039 99023039 401045.516 0
write: 0 0 0 0 0 26229.572 0[/FONT][/COLOR]
[COLOR=#000000][FONT=HPRegular]Non-medium error count: 95944[/FONT][/COLOR]
[COLOR=#000000][FONT=HPRegular][GLTSD (Global Logging Target Save Disable) set. Enable Save with '-S on'][/FONT][/COLOR]
[COLOR=#000000][FONT=HPRegular]SMART Self-test log
Num Test Status segment LifeTime LBA_first_err [SK ASC ASQ]
Description number (hours)
# 1 Background long Completed - 58588 - [- - -]
# 2 Background long Completed - 58465 - [- - -]
# 3 Background short Completed - 58461 - [- - -]
# 4 Background long Completed - 11 - [- - -]
# 5 Background short Completed - 10 - [- - -][/FONT][/COLOR]
[COLOR=#000000][FONT=HPRegular]Long (extended) Self Test duration: 3072 seconds [51.2 minutes][/FONT][/COLOR]

```

---

### Post by tgalati4 on 2013-06-01
Have you cleaned out the machine and reseated all of the components?  It's possible that your RAID card is failing or not keeping up with the write speeds.  Does your RAID controller have a battery?  Is it new?  HP might have a diagnostic suite that you can burn to CD and run some tests on your hardware.

It's not clear from your post if this server has been running reliably for a while in 12.04 or if this is a new install with older hardware and you haven't gotten a reliable system at all.

The difference between 683GB and 740GB could reflect the disk space required for parity storage to support RAID5.  You really can't use that space for data.  Although 6*146 is 864GB, so I would think that is already taken into account.  So either this disk space deficit is real because of a bad disk or cable, or the RAID controller is having some issues.

Because your drives have 56K hours, they are not new.  Consumer drives are rated to 50K hours, and Server class drives are typically rated to 100K or more.

This is troubling:  **Non-medium error count: 95944**.  It could be a buffer problem on a single drive or the caching on the RAID card, or something else.

A failing power supply could have similar symptoms--the RAID card is trying to keep up, but battery-powered cache can only do so much.

---

### Post by Pedlar88 on 2013-06-01
I use to have a 11.04 install that was working just fine, but I haven't used this server in about a year and I acquired some used drives to use in it (I use to have 6x36gb).

The RAID controller does have a Battery Backed Cache, and the Array Controller is an Integrated Chip on the Mother Board.

The drives I'm using a Server Class drives.

I have taken apart and reseated the backplane for the drives, as well as the BBWC card for the Array. The insight Diagnostics for the HP SmartStart CD aren't showing any errors for the controller, or Battery.

The Array Configuration write/read speed is setup to 50/50. and the RAID stripe at 256kb

---

### Post by tgalati4 on 2013-06-01
Without history of the drives that you put in, it's possible that you have one bad/intermittent disk.  Set the drives to JBOD (just a bunch of disks) and test each one individually.  It's also possible that your RAID controller can't handle (or is not certified) to run on the 146GB drives.  These controllers have very tight tolerances, so you have to at least be aware of HP's recommendations.

---

### Post by Cheesehead on 2013-06-01
tgalati4 is right. It could be a lot of things, including (most commonly) a failing drive.

Do you want to spend a lot of time troubleshooting component by component to save money?
Or do you want to spend more money to save troubleshooting time?

---

