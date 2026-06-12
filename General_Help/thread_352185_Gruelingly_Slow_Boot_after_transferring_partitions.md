---
title: "Gruelingly Slow Boot after transferring partitions to new Hard Drive"
date: 2007-02-03
forum: General Help
---

### Post by thetictacaddict on 2007-02-03
When I installed Xubuntu Edgy, I used the alternate install disk to set up a volume group and two logical volumes on top of a RAID1 partition.  Today I decided I wanted to repartition my drive and give up on RAID and LVM for a little while.  I removed one of my 2 drives from the array with mdadm, created some new partitions on it, and copied my three partitions (/boot, /, and /home) with a few rounds of cp -a.  /boot was on a primary partition.  The other two were logical volumes.  I edited /etc/fstab and /boot/grub/menu.list, and installed GRUB on the drive.  I booted it up, and thought it wouldn't boot.  Once I waited long enough though, it finished booting and I am typing this message from my successfully booted computer.  There is one irritating problem:

To go from GRUB to GDM takes approximately 15 minutes.

Most of that time is spent on a black screen after I see the informative message, "Starting up RAIDs.  Please wait, the process might take a long time!"  I think the problem is that there are no RAID arrays to start up.  What steps can I take to help pinpoint the problem?

---

### Post by thetictacaddict on 2007-02-03
Okay, I fixed it.  From boot loader to login prompt now takes a much more reasonable 26 seconds.  If anybody is wondering, I unpacked my initrd image, deleted the file etc/mdadm/mdadm.conf and repacked it.  It took me a while to figure out how to do that, but it involved gzip. gunzip, cpio, and some trial and error.  I think I am satisfied for now, but here's a new question: what happens now if I upgrade to a newer kernel with dist-upgrade?

---

### Post by GoBieN on 2007-02-08
How about purging mdadm and reinstalling a blank version ? So the config files are standard again, without a raid setup.

---

### Post by thetictacaddict on 2007-02-08
Hey, good idea!  I tried it and it seems to have fixed the problem.

When I opened up Synaptic I found that I can't update linux-headers-386, but I'm not sure if that's related.

---

