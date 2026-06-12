---
title: "Hard drive failure. Can't access remaining RAID disc."
date: 2007-10-02
forum: General Help
---

### Post by elamericano on 2007-10-02
I don't know how to rebuild, so I want to backup some of the data before I attempt it, but I can't mount the remaining drive on its own - is its filesystem type "Software RAID component"?

I may not rebuild at all if I can't find a drive with the exact same geometry, so saving what I can from the remaining mirror should be my first goal. My motherboard uses an nVidia RAID controller.

---

### Post by az on 2007-10-02
If it's software raid, you don't need to have drives with the same geometry, just the same partition sizes.

---

### Post by david3d on 2007-10-02
Your post doesn't contain enough information to go on.

What raid level do you have and is it dead or just degraded?

Basically rebuilding a degraded raid means replacing the broken drive and partitioning it if necessary as well as setting the partition type to linux autodetect raid.

Then running mdadm -a /dev/<md#> /dev/<newdrive/partition>

At that point if you type cat /proc/mdstat you should see that it's rebuilding. 
--
David

---

### Post by fjgaude on 2007-10-02
Are you using dmraid to mount the array?

You are using raid1?

What does sudo fdisk -l show?

---

### Post by elamericano on 2007-10-11
Sorry for the late follow-up. I inherited this system, so I knew none of the raid commands. Hopefully this time I'll provide enough info.

It was a RAID 1. The larger partition on each drive was the mirror, but the boot partition was on the dead drive. The raid showed as degraded, but it wouldn't boot, so no rebuild. I have since moved it to a new system. Now the bios doesn't know the mirror is degraded. It shows healthy. Hopefully I can manually start the rebuild... and rebuild the empty drive, not the one with the data.

fdisk -l:
```
Disk /dev/sdb: 400.0 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1         131     1052226   83  Linux
/dev/sdb2             132       48641   389656575   fd  Linux raid autodetect

Disk /dev/sdc: 400.0 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1         131     1052226   82  Linux swap / Solaris
/dev/sdc2             132       48641   389656575   fd  Linux raid autodetect
```

cat /proc/mdstat:
```
Personalities : [raid0] 
unused devices: <none>
```

dmraid -r:
```
/dev/sdb: nvidia, "nvidia_gcfddibd", mirror, inconsistent, 781422766 sectors, data@ 0
/dev/sdc: nvidia, "nvidia_gcfddibd", mirror, inconsistent, 781422766 sectors, data@ 0

```

I don't know what will happen if I do "dmraid -ay", because that does not indicate that sdb2 is the partition that needs to be rebuilt.

---

### Post by dcstar on 2007-10-11
> **elamericano said:**
> Sorry for the late follow-up. I inherited this system, so I knew none of the raid commands. Hopefully this time I'll provide enough info.

It was a RAID 1. The larger partition on each drive was the mirror, but the boot partition was on the dead drive.
............
I don't know what will happen if I do "dmraid -ay", because that does not indicate that sdb2 is the partition that needs to be rebuilt.

If the "dead" drive is still accessible, you can copy the boot sectors to the good drive by using the **dd** command (or GParted for the whole partition).

Then the good drive should boot up and you can then access your data on the RAID partition.

---

### Post by elamericano on 2007-10-11
No, the BIOS no longer recognizes the dead drive. I now own a new doorstop.

Anyone know the right way to mount this mirror raid, where only one has data?

---

### Post by dcstar on 2007-10-12
> **elamericano said:**
> No, the BIOS no longer recognizes the dead drive. I now own a new doorstop.

Anyone know the right way to mount this mirror raid, where only one has data?

If the hardware of the two drives is identical - and the fault with the dead drive is in the electronics and not the mechanicals - you may want to try swapping the circuits from one drive to the other. This may be a "last resort" - but back up the partition with the data on it before you do this!

If the software mirror partition is just "real" data, then just changing the partition type with cfdisk may get you access to it - I don't know if this will work, but you can always change it back (I think....)

Edit: Looking at the setup for Linux software RAID, changing a RAID1 partition back to a Linux partition should work - this is just the reverse of setting it up in the first place.

---

### Post by elamericano on 2007-10-12
Thanks, I liked your suggestions. However, changing the partition type to 0x83 didn't work, because I still couldn't mount it. I'm wondering if it is possible that this was a RAID 0. Is there a way to test?

I am going to try the swap the electronics idea too. If I can clone the dead drive, maybe this will boot after all.

So, for mounting the raid 1, do people think 'dmraid -ay' is the right way? Will it recognize which drive is empty and prompt me to start rebuilding? So far nothing is happening automatically :(

---

### Post by elamericano on 2007-10-12
Ok, with my data backed up I tried mounting the raid 1. As noted before:

/dev/sdb: nvidia, "nvidia_gcfddibd", mirror, inconsistent, 781422766 sectors, data@ 0
/dev/sdc: nvidia, "nvidia_gcfddibd", mirror, inconsistent, 781422766 sectors, data@ 0

maybe this is why dmraid -ay didn't work.

The next step is to reformat and get on with my life. If anyone has a last minute suggestion, I would sure appreciate it. My advice to those who would use one of these cheap motherboard raid solutions....don't. You'll double your disk space, and at least you'll have half your data if a drive goes bad.

---

### Post by david3d on 2007-10-22
Ok I'm trying to catch up on this thread now.  Hopefully not too late.  If this was a RAID1 mirror then all the data is on both drives.  You can simply mount one of the partitions completely ignoring the fact that it was a RAID volume and access the data.  If this is a degraded RAID5 then you should be able to get it started and mount it while it's degraded and either give it a new device to rebuild or backup the data.

Dmraid is the older set of user space tools for managing dm devices and mdadm is generally considered the tool to use for this stuff now.  In my opinion mdadm is a much better tool.

You can have a look at the metadata on the remaining drives to determine exactly what type of raid you had and what role each device played in the array.  The following commands will print out the information about the raids from the raid metadata to the screen.  Once we have a better idea of what you have we can figure out what options you have.

sudo mdadm -E /dev/sdb2
sudo mdadm -E /dev/sdc2

--
David

---

### Post by elamericano on 2007-10-30
Thanks David, I had to wipe the disk and get on with my life. I did try several more things, but eventually decided it was futile. I appreciate your information on reading the metadata. It may come in handy if my new RAID1 goes down. :shock:

It's OK really. The only thing I can't stand to lose is photos, and for that reason they're always backed up in multiple locations.

---

