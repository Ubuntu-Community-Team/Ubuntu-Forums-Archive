---
title: "Unable to mount RAID array"
date: 2016-10-19
forum: General Help
---

### Post by drexvictor-s on 2016-10-19
[COLOR=#111111][FONT=Ubuntu]As stated in the title, I am unable to mount my RAID array. Here is my mdadm.conf:

[/FONT][/COLOR]```
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
ARRAY /dev/md127  metadata=1.1 UUID=7228e3bb:e2927657:05bd319c:a646a849 name=dc.sec.net:0

# This file was auto-generated on Tue, 27 Sep 2016 20:52:52 +0530
# by mkconf $Id$
```

[COLOR=#111111][FONT=Ubuntu]Here is the result of my mount command sudo mount /dev/md127 /media/md[/FONT][/COLOR]

[COLOR=#111111][FONT=Consolas]```
mount: wrong fs type, bad option, bad superblock on /dev/md127,
```[/FONT][/COLOR]```
       missing codepage or helper program, or other error

       In some cases useful info is found in syslog - try [COLOR=#111111][FONT=Consolas]       dmesg | tail or so.[/FONT][/COLOR]
```

[COLOR=#111111][FONT=Ubuntu]Upon inspecting syslog I notice

[/FONT][/COLOR]```
[COLOR=#111111][FONT=Consolas]46065.060940] md127: bitmap initialized from disk: read 1 pages, set 0 of 29805 bits[/FONT][/COLOR]
Oct 17 12:05:26 irj-SandyBridge-Platform kernel: [246065.133456] md127: detected capacity change from 0 to 2000129359872
Oct 17 14:04:52 irj-SandyBridge-Platform kernel: [253230.799354] md127: detected capacity change from 2000129359872 to 0 [COLOR=#111111][FONT=Consolas]Oct 17 14:04:52 irj-SandyBridge-Platform kernel: [253230.799371] md: md127 stopped.[/FONT][/COLOR]
```[COLOR=#111111][FONT=Ubuntu]
[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]I tried to run fsck and got[/FONT][/COLOR]
```
[COLOR=#111111][FONT=Consolas]fsck from util-linux 2.27.1[/FONT][/COLOR]
e2fsck 1.42.13 (17-May-2015)
ext2fs_open2: Bad magic number in super-block
fsck.ext2: Superblock invalid, trying backup blocks...
fsck.ext2: Bad magic number in super-block while trying to open /dev/md127

The superblock could not be read or does not describe a valid ext2/ext3/ext4
filesystem.  If the device is valid and it really contains an ext2/ext3/ext4
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>
 or [COLOR=#111111][FONT=Consolas]    e2fsck -b 32768 <device>[/FONT][/COLOR]
```

[COLOR=#111111][FONT=Ubuntu]I have run both e2fsck -b 8193 /dev/md127 and e2fsck -b 32768 /dev/md127 and got the following result.

```
[FONT=Consolas]e2fsck 1.42.13 (17-May-2015)[/FONT]
```[/FONT][/COLOR]```

e2fsck: Bad magic number in super-block while trying to open /dev/md127

The superblock could not be read or does not describe a valid ext2/ext3/ext4
filesystem.  If the device is valid and it really contains an ext2/ext3/ext4
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>
 or [COLOR=#111111][FONT=Ubuntu][FONT=Consolas]    e2fsck -b 32768 <device>[/FONT][/FONT][/COLOR]
```[COLOR=#111111][FONT=Ubuntu]

Any ideas on how to fix this and recover the data would be much appreciated!

[/FONT][/COLOR]

---

### Post by SeijiSensei on 2016-10-19
Did you format the filesystem on the array after you assembled it using something like
```
sudo fsck -t ext4 /dev/md127
```

---

### Post by frostschutz on 2016-10-19
well, what's on it in the first place?

```

cat /proc/mdstat
sudo file -s /dev/md*

```

---

### Post by coffeecat on 2016-10-19
From the large heading to the Ubuntu, Linux and OS Chat sub-forum: "this sub-forum is for chat, not support... If you need technical help, please post in an appropriate support sub-forum."

*Thread moved to **General Help**.*

---

