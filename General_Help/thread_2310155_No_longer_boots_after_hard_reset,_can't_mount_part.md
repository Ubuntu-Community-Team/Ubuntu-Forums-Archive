---
title: "No longer boots after hard reset, can't mount partitions"
date: 2016-01-16
forum: General Help
---

### Post by walawa on 2016-01-16
Hi, 
I have a computer running ubuntu 14.04 that I was using media centre, and right now it's unable to boot and I'm worried the disk might be damaged. I'm a novice user and could really use some help.

Here are the details of what happened: This morning I was logged in over SSH and I noticed some lag and hanging, so went over to the machine and logged onto the desktop. There was a dialog warning of a system error, and the OS was not very responsive, especially the file manager, so I initiated a reboot. At that point, the system just hung for several minutes and I did a hard shutdown. When I tried to boot it up again, the following error message appeared before it started: "attempt to read or write outside of disk hd0", followed by "press any key to continue" which led to a blank screen. I rebooted the machine again, which now resulted in a GRUB menu. Selecting ubuntu leads to the message "Gave up waiting for root device" and enters an "initramfs" shell. 

I booted from a USB drive and opened GParted. It shows my drive as 'unallocated', and doesn't seem to recognize the partitions. I tried running 'fsck -y -f /dev/sdb' (sdb is this drive), resulting in "Attempt to read block from filesystem resulted in short read while trying to open /dev/sdb Could this be a zero-length partition?". After this failed, I ran 'boot-repair', which generated this output: [http://paste.ubuntu.com/14531747/](http://paste.ubuntu.com/14531747/). I don't know how to interpret most of this, but am worried about the I\O errors it throws with sdb! It did correctly list the partitions under the 'lsblk' section: I had a 40G partition for the system and a partition with the remaining space for storage. 

I'd like to repair the disk so that I can clone it and keep my system, but at very least I need to be able to recover the storage partition and hopefully my user data. 
Is this still possible? What should I do now?

---

