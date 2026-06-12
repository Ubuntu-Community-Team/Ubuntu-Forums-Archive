---
title: "3TB Hard drive (wd red) healthy or dead?"
date: 2013-01-27
forum: General Help
---

### Post by sdpagent on 2013-01-27
I have a hard drive that reports 'SMART capable status BAD' at boot. But if I plug in the drive and run an extended smart test, it passed without errors see [here]("http://pastebin.com/raw.php?i=epLSzsN6")
  
I am unable to see the volumes in Gparted (after plugging them in after OS loaded) but can see them in disk utility. I have been unable to run secure-erase or any formatting operations on them. Is there a clue in that output above? These drives are brand new and were in  a software raid array, so whatever happened to the first obviously broke the second (exact same problem)

Stu

---

### Post by TheFu on 2013-01-27
I would run **Boot-Info** to gather data about the drive: [https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

That should help diagnose the root cause.

Always use **parted** or** gparted** with 12.04 or later releases for these large HDDs.

---

### Post by sdpagent on 2013-01-27
I am running ubuntu 12.04.
The devices are not picked up by gparted.
These drives are just holding data. There is no boot data on them. I boot from a separate drive.

Stu

---

### Post by TheFu on 2013-01-27
> **sdpagent said:**
> I am running ubuntu 12.04.
The devices are not picked up by gparted.
These drives are just holding data. There is no boot data on them. I boot from a separate drive.

Understood, but boot-info will dump information about the disk layout and flags too.  I thought it would be helpful.

---

### Post by tgalati4 on 2013-01-27
Time to start looking at cables, power connections, etc.  It could be the drives just need breaking in. 

If the drives are enumerated with 

```
sudo fdisk -l
```

Then run badblocks on each drive.  Capture the output, cut and paste into a notepad.

```
sudo badblocks /dev/sde1
```

If you get a lot of badblocks, then run again can mark them as bad in the filesystem:

```
sudo fsck -cc /dev/sde1
```

If your drive can't run badblocks, then you really do have a bad drive.  Since these drives are new, I would return them.  If they are out-of-specification, they will bite you in the future.

Do a search on your particular model number and see if others are having similar problems.  Sometimes drive manufactures try to cut costs and use cheaper parts and catfood in their drives.

---

### Post by oldfred on 2013-01-27
I do not know RAID, but you cannot see RAID drives in gparted as it does not handle RAID.

       Do not use gparted on RAID.
[http://www.howtoforge.com/how-to-resize-raid-partitions-shrink-and-grow-software-raid](http://www.howtoforge.com/how-to-resize-raid-partitions-shrink-and-grow-software-raid)
Don't bother with RAID 0 unless you have a specific need for speed without data redundancy, since if one drive goes out, you lose the whole array.
[http://en.wikipedia.org/wiki/RAID](http://en.wikipedia.org/wiki/RAID)
parted (3.0) completely removes filesystem creation and modification support, except for filesystem probing to determine what's in a partition.

---

### Post by sdpagent on 2013-01-28
To answer a few questions
 - the drives **were** (as in no longer) in a sofware raid array, but mdadm does not pick them up anymore (no superblock found) and the conf file looks like its new for some reason. Very strange.

- fdisk does not pick up the drives

- i tried the drives in another machine (but running off of the same power (had the towers next to each other and just plugged in different sata cables into the other motherboard. I couldnt boot with the drives in that one either. (could this really be power related? I can hear the drives spin up when i plug in. They dont make a tick sound but a nice/clean sound (hard to explain). I guess I shouldn't hear them spin up at all though? 

The drives were working until I plugged in another drive a 2tb black and rebooted.

---

### Post by TheFu on 2013-01-28
> **sdpagent said:**
> - fdisk does not pick up the drives

**fdisk is not safe to use** on drives over 2TB in size or with GPT partitioning. This applies to fdisk-based tools like cfdisk and sfdisk as well.

Use** parted** or gparted going forward.

There is something about using a HDD in RAID that changes it - at least if the HDD wasn't partitioned. That is the flag that you need to get reset.  I'd use **parted** and write a new GPT partition to it. It isn't like you have anything to loose.  Don't use MBR partitions - it doesn't support drives a little over 2TB either.

Then I'd run spinrite (commercial software) on the HDDs to find any parts that cannot be read and give the HDD a chance to relocate any bad sectors. You can probably do this using something like **ddrescue** too.  

If the HDDs do not show up in the device table at all, then I'd verify that your BIOS sees them and look for MB and chipset driver updates. 

Sorry, I didn't go back and re-read prior messages to see exactly what you can and cannot see.

---

### Post by oldfred on 2013-01-28
Hard drives retain RAID meta-data, you have to remove that for gparted to then see drive.

Presence1960 on remove old raid setting from HD
[http://ubuntuforums.org/showthread.php?t=1325650](http://ubuntuforums.org/showthread.php?t=1325650)
sudo dmraid -E -r /dev/sda
sudo dmraid -E -r /dev/sdb
Also check BIOS for raid settings
More discusion:
[http://wwww.ubuntuforums.org/showthread.php?p=9274738#post9274738](http://wwww.ubuntuforums.org/showthread.php?p=9274738#post9274738)

---

### Post by sdpagent on 2013-01-28
> **TheFu said:**
> **fdisk is not safe to use** on drives over 2TB in size or with GPT partitioning. This applies to fdisk-based tools like cfdisk and sfdisk as well.

Use** parted** or gparted going forward.

There is something about using a HDD in RAID that changes it - at least if the HDD wasn't partitioned. That is the flag that you need to get reset.  I'd use **parted** and write a new GPT partition to it. It isn't like you have anything to loose.  Don't use MBR partitions - it doesn't support drives a little over 2TB either.

Then I'd run spinrite (commercial software) on the HDDs to find any parts that cannot be read and give the HDD a chance to relocate any bad sectors. You can probably do this using something like **ddrescue** too.  

If the HDDs do not show up in the device table at all, then I'd verify that your BIOS sees them and look for MB and chipset driver updates. 

Sorry, I didn't go back and re-read prior messages to see exactly what you can and cannot see.

I dont know if this is useful but
 - the drives were originally fine with being detected by the motherboard, so I know its not a motherboard driver issue.
 - I cant get into the bios when the drives are connected at time of boot
 - getting into the bios and then plugging in the drives, the motherboard does allow the drives to be seen, I dont know if the bios should update the list of drives when AHCI is on?

---

### Post by tgalati4 on 2013-01-28
It's possible that your 12VDC rail is sagging when all of your drives are plugged in.  That would cause the drives to underspin and appear not healthy.  Measure with a meter or use the BIOS Health Monitor to check voltages.  Unplug everything and test one drive a time.  The fact that you can't get into BIOS with all of the drives plugged in could be because the BIOS is waiting for the drives to report--and they don't because they haven't reached full speed.

---

### Post by TheFu on 2013-01-28
> **sdpagent said:**
> I dont know if this is useful but
 - the drives were originally fine with being detected by the motherboard, so I know its not a motherboard driver issue.
 - I cant get into the bios when the drives are connected at time of boot
 - getting into the bios and then plugging in the drives, the motherboard does allow the drives to be seen, I dont know if the bios should update the list of drives when AHCI is on?


[LIST]
[*]You can't see the drives in the BIOS and they are connected to the MB SATA ports?  If you don't see them inside the BIOS, then you have bigger issues.  This is just scary.  Anything related to power could be the issue. I've had a failing GPU impact system stability, even a new PSU didn't solve it.
[*]Or are you using another SATA controller? If this is true, then I'd never expect to see the drives in the MB BIOS.
[/LIST]
This stuff is much more important than any of your other issues, methinks.

---

