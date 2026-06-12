---
title: "Raid array not assemblying properly on boot"
date: 2013-10-20
forum: General Help
---

### Post by griztown on 2013-10-20
Hi all,

I have two raid 1 arrays and another raid 5 array. I reboot my computer recently and on boot I saw an LVM error. It appears my raid array wasn't build correctly. Here's what I see in dmesg

> 
[    1.962502] udevd[123]: starting version 175
[    1.964525] md: linear personality registered for level -1
[    1.966703] md: multipath personality registered for level -4
[    1.968019] md: raid0 personality registered for level 0
[    1.969541] md: raid1 personality registered for level 1
[    1.970692] async_tx: api initialized (async)
[    1.973904] pata_via 0000:03:00.0: version 0.3.4
[    1.973919] pata_via 0000:03:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.973957] pata_via 0000:03:00.0: setting latency timer to 64
[    1.974341] scsi6 : pata_via
[    1.974887] scsi7 : pata_via
[    1.975065] ata7: PATA max UDMA/133 cmd 0xd040 ctl 0xd030 bmdma 0xd000 irq 16
[    1.975067] ata8: PATA max UDMA/133 cmd 0xd020 ctl 0xd010 bmdma 0xd008 irq 16
[    1.975219] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    1.975233] r8169 0000:05:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    1.975259] r8169 0000:05:00.0: setting latency timer to 64
[    1.975319] r8169 0000:05:00.0: irq 54 for MSI/MSI-X
[    1.975629] r8169 0000:05:00.0: eth0: RTL8168e/8111e at 0xffffc90000c7a000, bc:ae:c5:e1:3d:db, XID 0c200000 IRQ 54
[    1.975632] r8169 0000:05:00.0: eth0: jumbo features [frames: 9200 bytes, tx checksumming: ko]
[    2.034869] raid6: int64x1   3229 MB/s
[    2.051292] hub 1-1:1.0: USB hub found
[    2.051434] hub 1-1:1.0: 6 ports detected
[    2.086231] md: bind<sda1>
[    2.088538] md: bind<sda6>
[    2.089510] md: bind<sda5>
[    2.102835] raid6: int64x2   4299 MB/s
[    2.105602] md: bind<sdb1>
[    2.106683] bio: create slab <bio-1> at 1
[    2.106686] md0: WARNING: sda6 appears to be on the same physical disk as sda5.
[    2.106688] md0: WARNING: sda1 appears to be on the same physical disk as sda5.
[    2.106689] md0: WARNING: sda1 appears to be on the same physical disk as sda6.
[    2.106690] True protection against single-disk failure might be compromised.
[    2.106723] md/raid1:md0: active with 2 out of 2 mirrors
[    2.106735] md0: detected capacity change from 0 to 498794496
[    2.107622]  md0: unknown partition table
[    2.112404] md: bind<sdb5>
[    2.113302] md/raid1:md1: active with 1 out of 2 mirrors
[    2.113311] md1: detected capacity change from 0 to 199864745984
[    2.124431] md: bind<sdb6>
[    2.130101]  md1: unknown partition table
[    2.165745] md: bind<sdc5>
[    2.166807] usb 2-1: new high-speed USB device number 2 using ehci_hcd
[    2.170817] raid6: int64x4   3471 MB/s
[    2.238748] raid6: int64x8   3005 MB/s
[    2.254746] Refined TSC clocksource calibration: 3411.482 MHz.
[    2.254750] Switching to clocksource tsc
[    2.306703] raid6: sse2x1    7337 MB/s
[    2.374670] raid6: sse2x2    8547 MB/s
[    2.442635] raid6: sse2x4    9153 MB/s
[    2.442637] raid6: using algorithm sse2x4 (9153 MB/s)
[    2.443099] xor: automatically using best checksumming function: generic_sse
[    2.462611]    generic_sse: 16948.000 MB/sec
[    2.462612] xor: using function: generic_sse (16948.000 MB/sec)
[    2.463227] hub 2-1:1.0: USB hub found
[    2.463312] hub 2-1:1.0: 8 ports detected
[    2.463726] md: raid6 personality registered for level 6
[    2.463727] md: raid5 personality registered for level 5
[    2.463729] md: raid4 personality registered for level 4
[    2.463806] md/raid:md2: device sdc5 operational as raid disk 2
[    2.463808] md/raid:md2: device sdb6 operational as raid disk 1
[    2.464003] md/raid:md2: allocated 3228kB
[    2.464021] md/raid:md2: raid level 5 active with 2 out of 3 devices, algorithm 2
[    2.464083] RAID conf printout:
[    2.464084]  --- level:5 rd:3 wd:2
[    2.464085]  disk 1, o:1, dev:sdb6
[    2.464086]  disk 2, o:1, dev:sdc5
[    2.464101] md2: detected capacity change from 0 to 1599136071680
[    2.526295]  md2: unknown partition table
[    2.546194] md: raid10 personality registered for level 10


md0 appears to be fine but md1 (which should have two disks in raid1) didn't add /dev/sda5 and md2 (which should have three disks in raid5) didn't add /dev/sda6. I've tried adding them in using

```
sudo mdadm --manage /dev/md1 --add /dev/sda5
```

but it keeps telling me 

```
mdadm: Cannot open /dev/sda5: Device or resource busy
```

The disk utility in Ubuntu tells me sda is healthy. So I'm not sure how things got out of sync. I've read that mdadm.conf could get out of sync and cause problems. Here's what it currently looks like.

> 
# mdadm.conf
#
# Please refer to mdadm.conf(5) for information about this file.
#

# by default (built-in), scan all partitions (/proc/partitions) and all
# containers for MD superblocks. alternatively, specify devices to scan, using
# wildcards if desired.
#DEVICE partitions containers

# auto-create devices with Debian standard permissions
CREATE owner=root group=disk mode=0660 auto=yes

# automatically tag new arrays as belonging to the local system
HOMEHOST <system>

# instruct the monitoring daemon where to send mail alerts
MAILADDR root

# definitions of existing MD arrays
ARRAY /dev/md/0 metadata=1.2 UUID=a04b3379:480ef690:b365aeb3:aacd93e7 name=ubuntu-main:0
ARRAY /dev/md/1 metadata=1.2 UUID=c6662562:50dc0b26:8dfcf367:dad97b53 name=ubuntu-main:1
ARRAY /dev/md/2 metadata=1.2 UUID=be00c1db:43eba4f8:4eacb439:420f9fa5 name=ubuntu-main:2

# This file was auto-generated on Sat, 22 Sep 2012 08:50:44 -0500
# by mkconf $Id$


Here's the output of mdadm --examine --scan
> 
$ sudo mdadm --examine --scan 
ARRAY /dev/md/0 metadata=1.2 UUID=a04b3379:480ef690:b365aeb3:aacd93e7 name=ubuntu-main:0
   spares=2
ARRAY /dev/md/1 metadata=1.2 UUID=c6662562:50dc0b26:8dfcf367:dad97b53 name=ubuntu-main:1
ARRAY /dev/md/2 metadata=1.2 UUID=be00c1db:43eba4f8:4eacb439:420f9fa5 name=ubuntu-main:2


Thanks in advance for your help!

---

### Post by griztown on 2013-10-20
I've also tried re-adding the dev
```
$ sudo mdadm --manage --re-add /dev/md1 /dev/sda5
mdadm: Cannot open /dev/sda5: Device or resource busy

```

From what I've seen reading google on this, it may mean I need to build a new initrd without the dmraid-driver. But that seems pretty serious so I was hoping to get a confirmation that I should go down that path.

Also, thought this might help.

```

$ cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md2 : active raid5 sdc5[2] sdb6[1]
      1561656320 blocks super 1.2 level 5, 512k chunk, algorithm 2 [3/2] [_UU]
      
md1 : active raid1 sdb5[1]
      195180416 blocks super 1.2 [2/1] [_U]
      
md0 : active raid1 sdb1[1] sda5[2](S) sda6[3](S) sda1[0]
      487104 blocks super 1.2 [2/2] [UU]

```

---

### Post by SaturnusDJ on 2013-10-20
Strange that warning that they are on the 'same physical disk.'

Let's do a little more debugging first.
Can you post the --examine output for all the members?

---

### Post by griztown on 2013-10-21
Yeah, that had me scratching my head too. Then I realized that when I was first trying to figure this out I had tried to add sda5 and sda6 to md0. Turns out they were still on that array as spares. Once I removed them I was able to add them to their proper arrays. Still unclear what happened to cause this but things seem to be working well. Thanks for the help.

---

