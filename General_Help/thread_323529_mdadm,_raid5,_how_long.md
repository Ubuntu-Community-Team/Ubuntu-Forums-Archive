---
title: "mdadm, raid5, how long?"
date: 2006-12-22
forum: General Help
---

### Post by vdhagen on 2006-12-22
Hi,
maybe I shouldn't try so set up a raid5 array being a ubuntu newbie, however, here's where I'm stuck:

I started 
sudo mdadm -C --auto=yes /dev/md0 -v -l5 -n4 /dev/hd[abcd]1
about 14 hours ago.

Ever since then, then harddisks are "busy". I can't start gparted (scans forever). I don't know how to find out what is happening on the system. Could it take that long? Can I stop the process and restart it later?

The harddisks are four IDE-250GB disks. The system is on an 8GB SCSI Harddisk (sda) attached to an adaptec 2940. The system is a Pentium III 1GHz, memory 512MB. Kernel is 2.6.17-10.

Any helpful comment will be greatly appreciated.

Oskar von dem Hagen

---

### Post by pwrstick on 2006-12-23
Well, I'm a nub too.  This is what I ran:

sudo mdadm --create /dev/md0 --level=5 --raid-devices=3 /dev/sd[acd]1 --add

I took roughly 60 minutes to build the array.  In this case there are 3 200GB SATA1.5 disks.  As I understand it Ram can be a huge factor, but we have the same amount.  Here's what else it's running on:

1.8GHz Sempron
512MB DDR Ram

**Go to /proc and run a 'more mdstat' to see how it's doing.**

---

### Post by vdhagen on 2006-12-28
Apparently the last drive was defect. :-(

With the remaining 3 drives the creation the process succeeded but still took approximately 4 hours.

Oskar von dem Hagen

---

