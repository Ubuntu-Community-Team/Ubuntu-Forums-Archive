---
title: "Mdadm RAID 5 array crashed, rebuild seems to work then stops"
date: 2014-03-11
forum: General Help
---

### Post by Arthurand on 2014-03-11
Hello, I am new here and I don't know if I am posting this in the correct section, pardon me if I am wrong.

I have a "deskserver" (desktop server) Core 2 Duo E7400 4GB RAM running Ubuntu 10.04 LTS x64 with a RAID 5 array of 6 SATA 500GB drives. The array is quite old, most of disks have 3.5 years of powered on hours. In the past, I've only had problems regarding SATA cables in which a simple reboot resolved the array problem, but it has been about two weeks it failed the first time for real.

Before this fail, /proc/mdstat was like that:

```
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md0 : active raid5 sdh1[3] sde1[4] sdf1[5] sdb1[0] sdd1[2] sdc1[1]
      2441834240 blocks level 5, 64k chunk, algorithm 2 [6/6] [UUUUUU]

unused devices: <none>
```

When it failed on March 1st 2014, that appeared:

```
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md0 : active raid5 sdh1[3] sde1[4] sdf1[5] sdb1[0] sdd1[6](F) sdc1[7](F)
      2441834240 blocks level 5, 64k chunk, algorithm 2 [6/4] [U__UUU]

unused devices: <none>
```

So, I rebooted the machine and it is like this now:

```
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md0 : active raid5 sdc1[1] sdb1[6](S) sdg1[5] sdf1[4] sde1[7](F) sdd1[2]
      2441834240 blocks level 5, 64k chunk, algorithm 2 [6/4] [_UU_UU]

unused devices: <none>
```

This machine has the bad habit of changing drive letters so I don't always know exactly the drives although sometimes I take note of their serial numbers and I can locate them physically.

The situation is the following, everytime I reboot the machine, it lists all drives as spare and as soon as I enter the command "mdadm --assemble --scan --force" it starts rebuilding and **apparently** I can access all my data. But when rebuild reaches 21.2%:

```
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md0 : active raid5 sdc1[1] sdb1[6] sdg1[5] sdf1[4] sde1[3] sdd1[2]
      2441834240 blocks level 5, 64k chunk, algorithm 2 [6/4] [_UU_UU]
      [====>................]  recovery = 21.2% (103692672/488366848) finish=286.4min speed=22379K/sec

unused devices: <none>
```

The rebuild fails, I get partial access to my data and it goes this state back again:

```
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md0 : active raid5 sdc1[1] sdb1[6](S) sdg1[5] sdf1[4] sde1[7](F) sdd1[2]
      2441834240 blocks level 5, 64k chunk, algorithm 2 [6/4] [_UU_UU]

unused devices: <none>
```

What should I do? I have a partial-backup on a Seagate USB 4TB drive. The backup is partially broken because the array failed during incremental backup and rsync got lost and deleted some files on backup drive because of I/O error.

I am afraid of just replacing the drive because of this wrongly marked spare drive and all.

Thanks for any help

---

### Post by TheFu on 2014-03-11
First - versioned backups, not just a mirror.

Second - you need to replace the failed disks ASAP.  I'd replace any suspect cables too. Disable the array and pull the cables between boots to see which is which if necessary. Do it ASAP.

Use UUIDs for your partitions going forward, not devices that change order.

ASAP, start doing versioned backups with something like rdiff-backup, duplicity or rsync+hardlinks.

---

### Post by Arthurand on 2014-03-12
Versioned backups, you mean at least two backups or keep multiple versions of the same file?

You said to replace the failed **disks**. That is problem, if I replace both, part of my data will be lost forever. I guess that there is only one disk that is seriously damaged, because when I force a rebuild, I can **apparently** read all my data, but when it fails on 21.2% I get only partial access. I have to know which is the disk.

When I run the force rebuild command, the following message is shown:

```
root@Bt-Networks-Server:~# mdadm --assemble --scan --force
mdadm: metadata format 00.90 unknown, ignored.
mdadm: forcing event count in /dev/sde1(3) from 8786 upto 8794
mdadm: clearing FAULTY flag for device 2 in /dev/md0 for /dev/sde1
mdadm: /dev/md0 has been started with 5 drives (out of 6) and 1 spare.
```

I have one clue, when I force the rebuild, I saw on iostat that is /dev/sdb the only disk that is being written to:

```
avg-cpu:  %user   %nice %system %iowait  %steal   %idle
          12.22    0.00   27.93    1.50    0.00   58.35

Device:         rrqm/s   wrqm/s     r/s     w/s    rkB/s    wkB/s avgrq-sz avgqu-sz   await  svctm  %util
sda               0.00   128.50    0.00   40.00     0.00   674.00    33.70     0.39    9.62   7.12  28.50
sdc            9456.00     0.00  176.00    0.00 38528.00     0.00   437.82     0.19    1.08   0.65  11.50
sdd            9480.50     0.00  151.50    0.00 38528.00     0.00   508.62     0.20    1.29   0.73  11.00
sdb               0.00  9276.50    0.00  309.00     0.00 38848.00   251.44     0.76    2.57   1.36  42.00
dm-0              0.00     0.00    0.00  168.50     0.00   674.00     8.00     1.77   10.53   1.69  28.50
dm-1              0.00     0.00    0.00    0.00     0.00     0.00     0.00     0.00    0.00   0.00   0.00
sde            9443.50     0.00  188.00    0.00 38340.00     0.00   407.87     0.55    2.90   1.49  28.00
sdf            9271.50     0.00  360.00    0.00 38464.00     0.00   213.69     1.34    3.72   1.29  46.50
sdg            9247.50     0.00  382.50    0.00 38336.00     0.00   200.45     1.72    4.50   1.22  46.50
md0               0.00     0.00    0.00    0.00     0.00     0.00     0.00     0.00    0.00   0.00   0.00

Filesystem:               rkB_nor/s    wkB_nor/s    rkB_dir/s    wkB_dir/s    rkB_svr/s    wkB_svr/s     ops/s    rops/s    wops/s
```

Note that, from all the disks on the array, only sdb is being written, the others are only being read. And the curious is that sdb is the drive flagged as spare.

---

### Post by TheFu on 2014-03-12
> **Arthurand said:**
> Versioned backups, you mean at least two backups or keep multiple versions of the same file?


No - I mean use a modern backup tool that lets you have 60 days of daily backups for just a little over 1x the storage. Any change in the source will be reflected in the backups daily.

Mirrors are wasteful and unnecessary.

Clearly, for large media files that change all the time, this is NOT possible, but for the system itself and non-media files, 60+ days of backups should be less than 1.2x the original storage amount. That is how it works here across many servers.  My signature has links. I like rdiff-backup but there are lots of efficient backup tools these days. You should pick one that fits your needs.

If there are 2 disks failed - well - then you have already lost that data.  Get over it. Move on. Live in the now, not the past.  The longer you wait to replace the disks, the more likely another disk will fail and even more data will be lost.

Do you really need RAID?  Perhaps you do.  I have it on storage where virtual machines run, but the backups for those machines are NOT put on RAID anything. I want to survive 1 failure, not infinite numbers of failures. Just don't have the budget for that level of redundancy.

---

### Post by Arthurand on 2014-03-13
I will try your recommendations about backup and this open source solution: [http://www.bacula.org/](http://www.bacula.org/)

My backup drive is much larger than my RAID 5 array which I think that will allow these versioned backups even of media files.

Luckily I guess the most important part of my data is on my backup drive and only a few sectors of one of the raid drives have failed. I recovered some pieces of /var/log/messages when the failure occurred the first time:

```
Mar  1 06:04:28 Bt-Networks-Server kernel: [519763.130043] ata4: soft resetting link
Mar  1 06:04:33 Bt-Networks-Server kernel: [519768.190024] ata4.00: disabled
Mar  1 06:04:33 Bt-Networks-Server kernel: [519768.190027] ata4.01: disabled
Mar  1 06:04:33 Bt-Networks-Server kernel: [519768.190038] ata4: EH complete
Mar  1 06:04:33 Bt-Networks-Server kernel: [519768.190059] sd 3:0:0:0: [sdc] Unhandled error code
Mar  1 06:04:33 Bt-Networks-Server kernel: [519768.190062] sd 3:0:0:0: [sdc] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
Mar  1 06:04:33 Bt-Networks-Server kernel: [519768.190067] sd 3:0:0:0: [sdc] CDB: Read(10): 28 00 0d 7b 74 00 00 01 00 00
Mar  1 06:04:33 Bt-Networks-Server kernel: [519768.190095] sd 3:0:1:0: [sdd] Unhandled error code
Mar  1 06:04:33 Bt-Networks-Server kernel: [519768.190097] sd 3:0:1:0: [sdd] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
Mar  1 06:04:33 Bt-Networks-Server kernel: [519768.190101] sd 3:0:1:0: [sdd] CDB: Write(10): 2a 00 0a 47 5b e0 00 00 20 00
Mar  1 06:04:33 Bt-Networks-Server kernel: [519768.190148] sd 3:0:1:0: [sdd] Unhandled error code
Mar  1 06:04:33 Bt-Networks-Server kernel: [519768.190150] sd 3:0:1:0: [sdd] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
Mar  1 06:04:33 Bt-Networks-Server kernel: [519768.190154] sd 3:0:1:0: [sdd] CDB: Read(10): 28 00 0d 7b 74 00 00 00 80 00
Mar  1 06:04:33 Bt-Networks-Server kernel: [519768.190199] sd 3:0:0:0: [sdc] Unhandled error code
Mar  1 06:04:33 Bt-Networks-Server kernel: [519768.190201] sd 3:0:0:0: [sdc] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
Mar  1 06:04:33 Bt-Networks-Server kernel: [519768.190205] sd 3:0:0:0: [sdc] CDB: Read(10): 28 00 0d 7b 75 80 00 01 00 00
Mar  1 06:04:33 Bt-Networks-Server kernel: [519768.190254] sd 3:0:0:0: [sdc] Unhandled error code
Mar  1 06:04:33 Bt-Networks-Server kernel: [519768.190257] sd 3:0:0:0: [sdc] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
Mar  1 06:04:33 Bt-Networks-Server kernel: [519768.190268] sd 3:0:0:0: [sdc] CDB: Write(10): 2a 00 0a 47 5c 00 00 04 00 00
Mar  1 06:04:33 Bt-Networks-Server kernel: [519768.190306] sd 3:0:1:0: [sdd] Unhandled error code
Mar  1 06:04:33 Bt-Networks-Server kernel: [519768.190309] sd 3:0:1:0: [sdd] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
Mar  1 06:04:33 Bt-Networks-Server kernel: [519768.190313] sd 3:0:1:0: [sdd] CDB: Read(10): 28 00 0d 7b 75 00 00 01 68 00
Mar  1 06:04:33 Bt-Networks-Server kernel: [519768.190351] sd 3:0:1:0: [sdd] Unhandled error code
Mar  1 06:04:33 Bt-Networks-Server kernel: [519768.190354] sd 3:0:1:0: [sdd] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
Mar  1 06:04:33 Bt-Networks-Server kernel: [519768.190357] sd 3:0:1:0: [sdd] CDB: Write(10): 2a 00
Mar  1 06:04:33 Bt-Networks-Server kernel: [519768.190363] sd 3:0:0:0: [sdc] Unhandled error code
Mar  1 06:04:33 Bt-Networks-Server kernel: [519768.190365]  0a 47 5c 00 00 04 00 00
Mar  1 06:04:33 Bt-Networks-Server kernel: [519768.190374] sd 3:0:0:0: [sdc] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
Mar  1 06:04:33 Bt-Networks-Server kernel: [519768.190378] sd 3:0:0:0: [sdc] CDB: Write(10): 2a 00 0a 47 60 00 00 03 80 00
Mar  1 06:04:33 Bt-Networks-Server kernel: [519768.190490] sd 3:0:1:0: [sdd] Unhandled error code
Mar  1 06:04:33 Bt-Networks-Server kernel: [519768.190492] sd 3:0:1:0: [sdd] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
Mar  1 06:04:33 Bt-Networks-Server kernel: [519768.190496] sd 3:0:1:0: [sdd] CDB: Write(10): 2a 00 0a 47 60 00 00 03 80 00
Mar  1 06:04:33 Bt-Networks-Server kernel: [519768.190569] sd 3:0:0:0: [sdc] Unhandled error code
Mar  1 06:04:33 Bt-Networks-Server kernel: [519768.190572] sd 3:0:0:0: [sdc] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
Mar  1 06:04:33 Bt-Networks-Server kernel: [519768.190575] sd 3:0:0:0: [sdc] CDB: Write(10): 2a 00 3a 37 ce 00 00 00 08 00
Mar  1 06:04:33 Bt-Networks-Server kernel: [519768.190596] md: super_written gets error=-5, uptodate=0
Mar  1 06:04:33 Bt-Networks-Server kernel: [519768.190630] program smartctl is using a deprecated SCSI ioctl, please convert it to SG_IO
Mar  1 06:04:33 Bt-Networks-Server kernel: [519768.202815] program smartctl is using a deprecated SCSI ioctl, please convert it to SG_IO
Mar  1 06:04:33 Bt-Networks-Server kernel: [519768.206150] program smartctl is using a deprecated SCSI ioctl, please convert it to SG_IO
Mar  1 06:04:33 Bt-Networks-Server kernel: [519768.216034] program smartctl is using a deprecated SCSI ioctl, please convert it to SG_IO
Mar  1 06:04:33 Bt-Networks-Server kernel: [519768.707124] RAID5 conf printout:
Mar  1 06:04:33 Bt-Networks-Server kernel: [519768.707128]  --- rd:6 wd:4
Mar  1 06:04:33 Bt-Networks-Server kernel: [519768.707132]  disk 0, o:1, dev:sdb1
Mar  1 06:04:33 Bt-Networks-Server kernel: [519768.707135]  disk 1, o:0, dev:sdc1
Mar  1 06:04:33 Bt-Networks-Server kernel: [519768.707138]  disk 2, o:0, dev:sdd1
Mar  1 06:04:33 Bt-Networks-Server kernel: [519768.707140]  disk 3, o:1, dev:sdh1
Mar  1 06:04:33 Bt-Networks-Server kernel: [519768.707143]  disk 4, o:1, dev:sde1
Mar  1 06:04:33 Bt-Networks-Server kernel: [519768.707145]  disk 5, o:1, dev:sdf1
Mar  1 06:04:34 Bt-Networks-Server kernel: [519768.721302] RAID5 conf printout:
Mar  1 06:04:34 Bt-Networks-Server kernel: [519768.721308]  --- rd:6 wd:4
Mar  1 06:04:34 Bt-Networks-Server kernel: [519768.721313]  disk 0, o:1, dev:sdb1
Mar  1 06:04:34 Bt-Networks-Server kernel: [519768.721316]  disk 1, o:0, dev:sdc1
Mar  1 06:04:34 Bt-Networks-Server kernel: [519768.721319]  disk 3, o:1, dev:sdh1
Mar  1 06:04:34 Bt-Networks-Server kernel: [519768.721322]  disk 4, o:1, dev:sde1
Mar  1 06:04:34 Bt-Networks-Server kernel: [519768.721325]  disk 5, o:1, dev:sdf1
Mar  1 06:04:34 Bt-Networks-Server kernel: [519768.721338] RAID5 conf printout:
Mar  1 06:04:34 Bt-Networks-Server kernel: [519768.721340]  --- rd:6 wd:4
Mar  1 06:04:34 Bt-Networks-Server kernel: [519768.721342]  disk 0, o:1, dev:sdb1
Mar  1 06:04:34 Bt-Networks-Server kernel: [519768.721344]  disk 1, o:0, dev:sdc1
Mar  1 06:04:34 Bt-Networks-Server kernel: [519768.721347]  disk 3, o:1, dev:sdh1
Mar  1 06:04:34 Bt-Networks-Server kernel: [519768.721349]  disk 4, o:1, dev:sde1
Mar  1 06:04:34 Bt-Networks-Server kernel: [519768.721352]  disk 5, o:1, dev:sdf1
Mar  1 06:04:34 Bt-Networks-Server kernel: [519768.741329] RAID5 conf printout:
Mar  1 06:04:34 Bt-Networks-Server kernel: [519768.741333]  --- rd:6 wd:4
Mar  1 06:04:34 Bt-Networks-Server kernel: [519768.741338]  disk 0, o:1, dev:sdb1
Mar  1 06:04:34 Bt-Networks-Server kernel: [519768.741341]  disk 3, o:1, dev:sdh1
Mar  1 06:04:34 Bt-Networks-Server kernel: [519768.741344]  disk 4, o:1, dev:sde1
Mar  1 06:04:34 Bt-Networks-Server kernel: [519768.741347]  disk 5, o:1, dev:sdf1
Mar  1 06:04:34 Bt-Networks-Server kernel: [519768.741374] lost page write due to I/O error on md0
Mar  1 06:04:34 Bt-Networks-Server kernel: [519768.741384] lost page write due to I/O error on md0
Mar  1 06:04:34 Bt-Networks-Server kernel: [519768.741390] lost page write due to I/O error on md0
Mar  1 06:04:34 Bt-Networks-Server kernel: [519768.741396] lost page write due to I/O error on md0
Mar  1 06:04:34 Bt-Networks-Server kernel: [519768.741403] lost page write due to I/O error on md0
Mar  1 06:04:34 Bt-Networks-Server kernel: [519768.741416] lost page write due to I/O error on md0
Mar  1 06:04:34 Bt-Networks-Server kernel: [519768.741422] lost page write due to I/O error on md0
Mar  1 06:04:34 Bt-Networks-Server kernel: [519768.741428] lost page write due to I/O error on md0
Mar  1 06:04:34 Bt-Networks-Server kernel: [519768.741435] lost page write due to I/O error on md0
Mar  1 06:04:34 Bt-Networks-Server kernel: [519768.741466] lost page write due to I/O error on md0
Mar  1 06:04:34 Bt-Networks-Server kernel: [519768.779489] JBD2: Detected IO errors while flushing file data on md0-8
Mar  1 06:04:34 Bt-Networks-Server kernel: [519768.784928] JBD2: Detected IO errors while flushing file data on md0-8
```

As I monitor SMART status of my disks all the time and there were constantly messages about ata link soft reset, I also think the failure was caused not by a faulty drive, but by a faulty controller or cables or both.

This was the message generated yesterday on another rebuild attempt:

```
Mar 12 23:11:41 Bt-Networks-Server kernel: [702659.688737] ata6.00: configured for UDMA/133
Mar 12 23:11:41 Bt-Networks-Server kernel: [702659.688756] ata6: EH complete
Mar 12 23:11:45 Bt-Networks-Server kernel: [702663.593611] ata6.00: configured for UDMA/133
Mar 12 23:11:45 Bt-Networks-Server kernel: [702663.593623] ata6: EH complete
Mar 12 23:11:49 Bt-Networks-Server kernel: [702667.498276] ata6.00: configured for UDMA/133
Mar 12 23:11:49 Bt-Networks-Server kernel: [702667.498319] sd 6:0:0:0: [sde] Unhandled sense code
Mar 12 23:11:49 Bt-Networks-Server kernel: [702667.498321] sd 6:0:0:0: [sde] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Mar 12 23:11:49 Bt-Networks-Server kernel: [702667.498324] sd 6:0:0:0: [sde] Sense Key : Medium Error [current] [descriptor]
Mar 12 23:11:49 Bt-Networks-Server kernel: [702667.498327] Descriptor sense data with sense descriptors (in hex):
Mar 12 23:11:49 Bt-Networks-Server kernel: [702667.498329]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00
Mar 12 23:11:49 Bt-Networks-Server kernel: [702667.498335]         0c 5c 74 44
Mar 12 23:11:49 Bt-Networks-Server kernel: [702667.498338] sd 6:0:0:0: [sde] Add. Sense: Unrecovered read error - auto reallocate failed
Mar 12 23:11:49 Bt-Networks-Server kernel: [702667.498342] sd 6:0:0:0: [sde] CDB: Read(10): 28 00 0c 5c 73 00 00 03 00 00
Mar 12 23:11:49 Bt-Networks-Server kernel: [702667.498375] __ratelimit: 116 callbacks suppressed
Mar 12 23:11:49 Bt-Networks-Server kernel: [702667.498377] raid5:md0: read error not correctable (sector 207383616 on sde1).
Mar 12 23:11:49 Bt-Networks-Server kernel: [702667.498427] raid5:md0: read error not correctable (sector 207383624 on sde1).
Mar 12 23:11:49 Bt-Networks-Server kernel: [702667.498430] raid5:md0: read error not correctable (sector 207383632 on sde1).
Mar 12 23:11:49 Bt-Networks-Server kernel: [702667.498432] raid5:md0: read error not correctable (sector 207383640 on sde1).
Mar 12 23:11:49 Bt-Networks-Server kernel: [702667.498434] raid5:md0: read error not correctable (sector 207383648 on sde1).
Mar 12 23:11:49 Bt-Networks-Server kernel: [702667.498436] raid5:md0: read error not correctable (sector 207383656 on sde1).
Mar 12 23:11:49 Bt-Networks-Server kernel: [702667.498438] raid5:md0: read error not correctable (sector 207383664 on sde1).
Mar 12 23:11:49 Bt-Networks-Server kernel: [702667.498441] raid5:md0: read error not correctable (sector 207383672 on sde1).
Mar 12 23:11:49 Bt-Networks-Server kernel: [702667.498443] raid5:md0: read error not correctable (sector 207383680 on sde1).
Mar 12 23:11:49 Bt-Networks-Server kernel: [702667.498445] raid5:md0: read error not correctable (sector 207383688 on sde1).
Mar 12 23:11:49 Bt-Networks-Server kernel: [702667.498477] ata6: EH complete
Mar 12 23:11:49 Bt-Networks-Server kernel: [702667.624538] md: md0: recovery done.
Mar 12 23:11:49 Bt-Networks-Server kernel: [702667.848019] RAID5 conf printout:
Mar 12 23:11:49 Bt-Networks-Server kernel: [702667.848022]  --- rd:6 wd:4
Mar 12 23:11:49 Bt-Networks-Server kernel: [702667.848025]  disk 0, o:1, dev:sdb1
Mar 12 23:11:49 Bt-Networks-Server kernel: [702667.848026]  disk 1, o:1, dev:sdc1
Mar 12 23:11:49 Bt-Networks-Server kernel: [702667.848028]  disk 2, o:1, dev:sdd1
Mar 12 23:11:49 Bt-Networks-Server kernel: [702667.848030]  disk 3, o:0, dev:sde1
Mar 12 23:11:49 Bt-Networks-Server kernel: [702667.848031]  disk 4, o:1, dev:sdf1
Mar 12 23:11:49 Bt-Networks-Server kernel: [702667.848033]  disk 5, o:1, dev:sdg1
Mar 12 23:11:49 Bt-Networks-Server kernel: [702667.861334] RAID5 conf printout:
Mar 12 23:11:49 Bt-Networks-Server kernel: [702667.861337]  --- rd:6 wd:4
Mar 12 23:11:49 Bt-Networks-Server kernel: [702667.861340]  disk 1, o:1, dev:sdc1
Mar 12 23:11:49 Bt-Networks-Server kernel: [702667.861342]  disk 2, o:1, dev:sdd1
Mar 12 23:11:49 Bt-Networks-Server kernel: [702667.861344]  disk 3, o:0, dev:sde1
Mar 12 23:11:49 Bt-Networks-Server kernel: [702667.861346]  disk 4, o:1, dev:sdf1
Mar 12 23:11:49 Bt-Networks-Server kernel: [702667.861348]  disk 5, o:1, dev:sdg1
Mar 12 23:11:49 Bt-Networks-Server kernel: [702667.861362] RAID5 conf printout:
Mar 12 23:11:49 Bt-Networks-Server kernel: [702667.861363]  --- rd:6 wd:4
Mar 12 23:11:49 Bt-Networks-Server kernel: [702667.861364]  disk 1, o:1, dev:sdc1
Mar 12 23:11:49 Bt-Networks-Server kernel: [702667.861366]  disk 2, o:1, dev:sdd1
Mar 12 23:11:49 Bt-Networks-Server kernel: [702667.861367]  disk 3, o:0, dev:sde1
Mar 12 23:11:49 Bt-Networks-Server kernel: [702667.861369]  disk 4, o:1, dev:sdf1
Mar 12 23:11:49 Bt-Networks-Server kernel: [702667.861370]  disk 5, o:1, dev:sdg1
Mar 12 23:11:49 Bt-Networks-Server kernel: [702667.880094] RAID5 conf printout:
Mar 12 23:11:49 Bt-Networks-Server kernel: [702667.880098]  --- rd:6 wd:4
Mar 12 23:11:49 Bt-Networks-Server kernel: [702667.880100]  disk 1, o:1, dev:sdc1
Mar 12 23:11:49 Bt-Networks-Server kernel: [702667.880102]  disk 2, o:1, dev:sdd1
Mar 12 23:11:49 Bt-Networks-Server kernel: [702667.880104]  disk 4, o:1, dev:sdf1
Mar 12 23:11:49 Bt-Networks-Server kernel: [702667.880106]  disk 5, o:1, dev:sdg1
```

As this is a home storage and I don't have time during the week, this weekend I will try to do another rebuild and try pausing it in order to get my data accessible and copy it all over to another drive.

I don't know any other better solution than RAID for me. This is a home storage you know. It was the best solution I found to save all my data for posterity. I just wasn't counting the array would fail during an incremental backup and that it would corrupt this backup.

As this array is quite old and I still think RAID is the best solution for me, I was thinking about buying some 1TB drives and create another RAID 5 array this time with a spare disk and a better backup solution as you recommended. I am just affraid to buy larger drives because of some URE that can occur on large drives during a rebuild.

---

### Post by TheFu on 2014-03-13
RAID for media is overkill, IHMO.  Better backups are less complicated. You can still use aufs or similar to merge all the separate disks into 1, but perform backups outside that.  SnapRAID is an option too.

Backups of the OS, settings and non-media data need to be versioned. Backups of large media ... I just rsync like you, but with 10% par2 files to address any corruption that may happen.  That is the theory.  I've never tested it since switching to HDD for backups, but it has saved me about 20 times on optical media storage that failed.

I started RAIDing with 80G disks.  Moved to 320G and finally to 2TB.  I think the large-disk-rebuild-failure claims are overstated by folks who don't completely understand MTBF.  

RAID never replaces backups.

Oh ... and SMART data is of limited use in recognizing disk errors. Definitely keep watching it, but it is more about the change from week-to-week in the sector relocations than anything else. I perform weekly scrubs of my RAID arrays. This gives my a little warning if something bad is about to happen.  Had a disk failure a last month on a 14 month old 2tb HDD. Swapped it out that day and the rebuild took 12+ hrs.  I had versioned backups of that data too - on a different machine.

Switched from RAID5 to RAID1 in the last update.  Considered going to RAIDz2, but just couldn't justify the added cost for all the extra RAM that would require.  Backups are the main method of recovery - if the RAID fails, it is an inconvenience only.

Backula - that is a complex solution.  I was unable to get it working with a small amount of effort.

---

### Post by Arthurand on 2014-03-13
> I just rsync like you, but with 10% par2 files to address any corruption that may happen

What do you mean by par2 files?

> I perform weekly scrubs of my RAID arrays.

You mean SMART deep tests and checking reallocated sectors?

I was also thinking of RAIDz2 (RAID 6), but I don't know, it is too expensive...

I don't know which path I will take, I have a brand new 2TB SATA drive here already (Seagate STBD2000101).

As I already have this drive, I thought of buying at least another one and do a RAID 1 too, and, if the price is good, buy another to have as a spare.

---

### Post by TheFu on 2014-03-13
> **Arthurand said:**
> What do you mean by par2 files?
par2 is a parity tool. [http://blog.jdpfu.com/2011/06/12/optical-data-recovery-technique-with-ddrescue-and-par2](http://blog.jdpfu.com/2011/06/12/optical-data-recovery-technique-with-ddrescue-and-par2) explains.

> **Arthurand said:**
> 
You mean SMART deep tests and checking reallocated sectors? No. mdadm has a facility.
The root crontab:
```
12 3 * * 7 echo check > /sys/block/md1/md/sync_action
12 3 * * 2 echo check > /sys/block/md2/md/sync_action
```

> **Arthurand said:**
> 
I was also thinking of RAIDz2 (RAID 6), but I don't know, it is too expensive...
RAIDz2 != RAID6.  ZFS actually validates that what was sent to the HDD was actually written.

> **Arthurand said:**
> 
I don't know which path I will take, I have a brand new 2TB SATA drive here already (Seagate STBD2000101).
As I already have this drive, I thought of buying at least another one and do a RAID 1 too, and, if the price is good, buy another to have as a spare.

The drive that died here was a 2TB seagate - slightly different model. That is the 3rd time I've been burned by that company. They used to make the best HDDs ... something changed inside the company around the time they released the 600+G drives and lied about issues for 9+months to the public. Their quality has never been the same on non-enterprise HDDs, IMHO.  I have 1 big Seagate left and expect it to fail at any point. Best to have that feeling about every HDD, I suppose.
Been running WD black, blue, red and Hitachi drives the last few years .. besides those 2 seagates, now 1.  Just dropped a 4TB hitachi into my plex server last month. 

Backups (rsync) of the media goes over the network to a really slow USB2 dock as needed.  The OS, apps, and personal settings/files are backed up with rdiff-backup nightly.  That has been my backup tool of choice the last 4 yrs.  Had to restore a few times - only for servers - worked. I like that it is highly efficient in time, space and networking.  Most systems get 60 days of backups here, a few get 90 and some 30. It all depends on the risks to the system.  Anything internet facing gets 90 days, for example. Hopefully we will discover any breaches within 90 days.

---

