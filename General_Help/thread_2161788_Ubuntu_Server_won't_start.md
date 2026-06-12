---
title: "Ubuntu Server won't start"
date: 2013-07-11
forum: General Help
---

### Post by spiceygas on 2013-07-11
I'm running Ubuntu Server v12.04 as a headless file server.  I had a power outage that took down the server, and after powering it up again I cannot connect to it.  I hooked up a monitor and keyboard, and the BIOS posts fine and I can see the HDD containing the OS on the list of bootable devices. After the BIOS post... nothing.  Like, literally nothing.  It just sits at a blank screen.

No GRUB.  No error message.  No nothing.

Any ideas what to try?  I had been keeping it up-to-date by installing updates every 2-3 weeks, so nothing should be too ancient.



(I know my data isn't lost because I can login to the Areca RAID controller card and see that the partition is still there.  I just cannot get the OS running.)

---

### Post by spiceygas on 2013-07-12
By pressing random buttons I somehow got grub to start (No idea what I pressed) and started in recovery mode.

I've got a RAID1 of two identical drives that the OS is installed on.  It appears that one of them has failed.  cat /proc/mdstat yields:


```
md0 : active raid1 sda1[0]
       312438592 blocks super 1.2 [2/1] [U_]

unused devices: <none>
```


Doing mdadm --examine on the two partitions, they have significantly different checksums and events.  sda1 has 56627 events, while sdb1 has 230 events.


Is it safe to just mark the second HDD (sdb1) as failed and then re-add it to the RAID?  I doubt that the disk is actually damaged -- it probably just got out of sync when the power was pulled unexpectedly.

---

### Post by spiceygas on 2013-07-12
So I'm now running on the assumption that the problem is that the OS is on a degraded RAID1.  Since mdadm says it's Clean,Degraded, I think that if I repair the RAID then it will work.

I'm thinking about two options:

1. Zero out the superblock on the drive that dropped from the array (sdb) and then add it back in.  Let the rebuild do its thing from the good drive (sda).
2. Use the --re-add command to put sdb back into the array.


The first option seems more reliable since I'm not sure if there's a bitmap on the drive.  Sure, it'll take longer to rebuild but reliability is more important to me than leaving it for a while.  I talked it over with a couple of guys at work and they seem to agree, but none have actually done it before so I'd love a second opinion.


Also, after doing all of this do I need to install grub on the drive?  If so, how do I do that?

---

### Post by spiceygas on 2013-07-15
I fixed the problem.  Turns out that disk1 was still in-tact and disk2 had been knocked out of the RAID by the power outage.  I simply added disk2 back into the RAID, waited for it to resync, and then rebooted into the OS.  Everything is now dandy.

---

