---
title: "RAID1 arrays won't start when drive is missing"
date: 2007-11-21
forum: General Help
---

### Post by rlcarr on 2007-11-21
I've just installed a Gusty system as LVM-over-RAID1.

I have two RAID1 devices -- /dev/md0 which is /boot (and
does NOT use LVM) and is made up of /dev/sda2 and /dev/sdb2,
and /dev/md1 which has LVM (and the rest of the system) over it
and is made up of /dev/sda3 and /dev/sdb3.

I've grub'd both /dev/sda and /dev/sdb, and as long as
both drives are plugged in, I can boot from either drive
and everything works and is happy.

However...

When I try to boot with a drive removed (for testing purposes),
grub comes up fine and the system begins to boot, but it appears
that the arrays will not start, which means there's no root filesystem
available and everything grinds to a halt.  This doesn't seem right.
Given the nature of RAID1, the arrays darn well should start up even
with a missing drive.

The boot output when the drive is missing has:
   md: md0 stopped
   md: bind <sda2>
   md: md1 stopped
   md: md0 stopped
   md: unbind <sda2>
   md: export_rdev(sda2)
   md: bind <sda2>
   md: md1 stopped
   md: bind <sda3>
and then everything grinds to a halt.

When both drives are present, this section goes:
   md: md0 stopped.
   md: unbind<sdb2>
   md: export_rdev(sdb2)
   md: bind<sdb2>
   md: bind<sda2>
   raid1: raid set md0 active with 2 out of 2 mirrors
   md: md1 stopped.
   md: bind<sdb3>
   md: bind<sda3>
   raid1: raid set md1 active with 2 out of 2 mirrors

So why won't the arrays start up when a drive is missing (it doesn't
matter which drive is the missing one)?

---

### Post by rlcarr on 2007-11-22
Two other things I've discovered:

If while the system is running in normal mode I do:
mdadm /dev/md0 --fail /dev/sdb2 --remove /dev/sdb2
mdadm /dev/md1 --fail /dev/sdb3 --remove /dev/sdb3
and then shut down the machine and unplug the drive, then I can boot from the remaining drive.

So if the drive fails while the system is running, it can be punted from the array and the machine can boot off one drive. That's nice and all, but that doesn't help in the case where the drive fail event causes the machine to crash (say the drive dies and takes down the bus and the machine locks up).

Also...

on my machine if there is only a single drive present it registers as /dev/sda to both grub **and the kernel** no matter what SATA port/controller the remaining drive is plugged into.

---

### Post by fjgaude on 2007-11-22
I know what  you are saying... sometime back I was given some sage advice: don't boot from a raid array. I think I can begin to understand why. It's complicated and prone to error. So for many months I've used a single drive to boot, and use raid5 for data. That has worked just fine.

Over the months I've read of some many folks having troubles with raid1 booting from such. I've also heard that 7.10 has problems in this area, but can't say for sure.

Good luck with your ventures.

---

### Post by rlcarr on 2007-11-27
This seems to be relevant:

[https://bugs.launchpad.net/ubuntu/+source/mdadm/+bug/120375](https://bugs.launchpad.net/ubuntu/+source/mdadm/+bug/120375)

---

### Post by fjgaude on 2007-11-28
Well, until it is certain that raid1 works in Ubuntu I'll stick to booting from a single fast disk and using raid5 
with a soft link to that disk.

Yes, I've seen that bug report over time, and thanks.

---

