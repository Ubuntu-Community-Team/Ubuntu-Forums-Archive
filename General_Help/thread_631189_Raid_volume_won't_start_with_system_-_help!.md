---
title: "Raid volume won't start with system - help!"
date: 2007-12-04
forum: General Help
---

### Post by IanLowe on 2007-12-04
Okay, I have just finished building a Gutsy machine to use as a VMWare platform. I have six 500Gb drives, configured as follows:

sda1, sdb1, 20Gb each - /dev/md0 RAID1
sdc1 - swap, 20Gb
sdd1, sde1, sdf1 - 20Gb partitions not used at present

sda2,sdb2,sdc2,sdd2,sde2,sdf2 - 490Gb each, /dev/md1 RAID5

now, this was originally a RAID5 array of four drives, which I grew using the mdadm --grow command... the problem being that whilst it booted just fine with four disks, since I grew the raid array it fails to startup, complains that it can't do an fsck, and drops me into the maintenance shell during boot.

If I do an mdadm --detail /dev/mdo, that reports okay - if I do the same for /dev/md1 it says "/dev/md1 doesn't appear to be active".

mdadm --assemble /dev/md1 --auto doesn't work - it says "no devices found"

 if I do an explicit mdadm --assemble /dev/md1 /dev/sda2 /dev/sdb2 /dev/sdc2 /dev/sdd2 /dev/sde2 /dev/sdf2, then it becomes active correctly, fsck.ext3 /dev/md1 shows the fileystem clean, and I can mount the volume correctly and continue booting.

How can I make the raid array start up normally during boot? :confused:

---

### Post by ian dobson on 2007-12-04
Hi,

Make sure your mdadm.conf is setup correctly with "all" of your drives included.

mdadm.conf normally lives in /etc/mdadm.

Regards
Ian Dobson

---

### Post by IanLowe on 2007-12-04
Ahh right - that's the one. 

My mdadm.conf still contains a line that says num-devices=4. I'll get it updated (reading info mdadm.conf right now )

Thanks for the help!

Incidentally, this is one of those features that shows Ubuntu to be getting seriously mature - dynamically growing RAID5 volumes and filesystems online without paying hundreds of dollars on a high end hardware RAID card... awesome :)

---

### Post by fjgaude on 2007-12-04
Interesting... please give us the details when you get your system running as it should. The mdadm.conf file I do believe is read in the auto mode.

---

### Post by ian dobson on 2007-12-04
Hi,

Glad to be of service. 

I'm currently fighting with my 2Tb raid5 array (4x500Gb) the array starts up about 50% of the time without any problems, but that's for a different thread. Enough to say I've spent a long time playing with mdadm/mdadm.conf.

Regards
Ian Dobson

---

### Post by fjgaude on 2007-12-04
You know, after my raid5 was built and running awhile, at that time I was using its UUID in the fstab file, I switched to it /dev/md0 lable after Gutsy came out. You might try using one or the other and see what happens.

My understanding is Gutsy is much improved when it comes to handling drives, especially muliti ones, and as you add one more, maybe the UUID doesn't change. <sigh>

Keep us informed to your progress.

---

### Post by IanLowe on 2007-12-04
okay, nailed it..

according to the mdadm.conf info page, all elements on the config line for each array needs to match or it will not load, so in my case, although the UUID matched, the num-devices was wrong..

changed that to the right number of devices, and rebooted - pow! worked perfectly.

thanks for your help mate!

---

### Post by fjgaude on 2007-12-04
Wow, and congratulations... please mark this thread as [SOLVED].

Times tells, and each day we learn something that is helpful.

---

