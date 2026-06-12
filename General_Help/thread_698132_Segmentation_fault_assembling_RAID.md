---
title: "Segmentation fault assembling RAID"
date: 2008-02-15
forum: General Help
---

### Post by axcairns on 2008-02-15
Hey,

I have a RAID-5 array with 4 drives on my Gutsy (upgraded from Feisty) setup. This has worked fine for about 9 months but has now stopped working. When I try to manually assemble the array using the following command it fails with a segmentation fault -

```
allan@library:~$ sudo mdadm -A /dev/md2
Segmentation fault (core dumped)
```

This is my mdadm.conf -

```
# mdadm.conf
#
# Please refer to mdadm.conf(5) for information about this file.
#

# by default, scan all partitions (/proc/partitions) for MD superblocks.
# alternatively, specify devices to scan, using wildcards if desired.
DEVICE partitions

# auto-create devices with Debian standard permissions
CREATE owner=root group=disk mode=0660 auto=yes

# automatically tag new arrays as belonging to the local system
HOMEHOST <system>

# instruct the monitoring daemon where to send mail alerts
MAILADDR root

# definitions of existing MD arrays
ARRAY /dev/md2 level=raid5 num-devices=4 UUID=aa0c3671:ecd71858:b81716b9:370ff49e

# This file was auto-generated on Tue, 03 Jul 2007 12:12:36 +0800
# by mkconf $Id: mkconf 261 2006-11-09 13:32:35Z madduck $
```

I also tried manually specifying the component drives -

```
allan@library:~$ sudo mdadm --assemble /dev/md2 /dev/hda3 /dev/hdc3 /dev/hdd3 /dev/sda1
Segmentation fault (core dumped)
```

I also tried booting into a Gutsy livecd and got the same error.

I checked dmesg and /var/log/messages but didn't see anything which looked relevant. 

Any ideas?

Thanks,


Allan

---

### Post by astrotech226 on 2008-02-15
This is a long shot, but maybe mdadm tool needs upgraded or reinstalled.  Those tools are usually built against a particular kernel and your upgrades may have broken this.

See if in your Synaptic package manager if mdadm is of the lastest version.  If so, try to reinstall it and see what happens.

---

### Post by axcairns on 2008-02-16
mdadm is up to date but perhaps there is a bug in it? I am running memtest at the moment and, once that is done, I will try a Feisty livecd to see if the mdadm version in that repository has the same problem.

Thanks,

Allan

---

### Post by axcairns on 2008-02-16
Looks like one of the drives is faulty. By process of elimination I found that hdd3 appears to be the culprit. 

I was able to assemble the remaining drives (with the --force flag because I had no spares and was therefore trying to assemble the array with less than the required # of drives) and mount the array. 

Thanks,

Allan

---

