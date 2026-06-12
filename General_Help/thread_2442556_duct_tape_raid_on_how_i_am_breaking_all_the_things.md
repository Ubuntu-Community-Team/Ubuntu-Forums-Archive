---
title: "duct tape raid: on how i am breaking all the things in all the wrong ways"
date: 2020-05-04
forum: General Help
---

### Post by sideburnie on 2020-05-04
Some background: I have built many raids. I have learned to love mdadm and distrust hardware. I need some local backup on one of my servers and it has grown beyond single external hard drives into the tens of TB. The server that I have only has 2.5" bays, and I like the idea of being able to connect this cheap local storage to another computer in the event of a failure of the server. 

So. 

I looked at NASes. I reminded myself that I don't trust hardware. External NAS situations typically have a single proprietary power supply for example and/or a single proprietary SAS/esata card. In my previous life I would have just built out three complete network connected servers and ran Ceph with 10gig. But now I have zero budget. What was the most minimal while fast connection I could get? 

External hard drives each have their own power supply. They already have a high bandwidth low-ish latency general purpose connection--USB 3. What if I just soft-raid-sixed a bunch of 10TB external drives and got a USB 3.1 gen2 card. Looks like Highpoint makes a card: [https://highpoint-tech.com/USA_new/series-ru1344a-overview.htm](https://highpoint-tech.com/USA_new/series-ru1344a-overview.htm). I've used highpoint! They make decent stuff! 

You can probably see where this trainwreck is going. 

I `dd if=/dev/zero` the first few hundred gigs of each drive. I 

```
sudo mdadm --create --verbose /dev/md1 --level=6 --raid-devices=6 /dev/sda /dev/sdh /dev/sdi /dev/sdj /dev/sdk /dev/sdl
```

A day later; success! I have a /dev/md1! I 

```
sudo mkfs.ext4 /dev/md1 
```
```
sudo mount /dev/md1 /media/external 
```

Success! I 

```
dd if=/dev/urandom of=/tmp/noise.img
```

For about 10GB. And I 

```
time cp /tmp/noise.img /media/external/noise.img
```

back and forth. It's maxing out my boot SSD! 450MB/s both ways! Stoked! 

So. 

I start some reliability testing. I unplug one drive. I replug. I 

```
sudo mdadm /dev/md1 --re-add /dev/sda
```

Success! 

I reboot. This is where things start going down hill. I do a few more reboots combined with various pokery and futzing. 

Some things I have encountered through experimentation. 

1.  I cannot get en entry in /etc/mdadm/mdadm.conf to assign a /dev/md# across a reboot. The array always appears as md127 (the default for one unassigned). I have tried 

```

ARRAY /dev/md/computername:1 metadata=1.2 name=computername:1 UUID=${whatRULookinAt}
ARRAY /dev/md/1 metadata=1.2 name=computername:1 UUID=${whatRULookinAt}
ARRAY /dev/md1 metadata=1.2 name=computername:1 UUID=${whatRULookinAt}

```

It does however mount fine using the linked dev name like 
```
sudo mount /dev/md/computername:1 /media/external
```

Do I fail to get a /dev/md1 assignment because they are USB drives and taking too long to start or something similar? From what I had read on the internet prior to getting started, I should be fine with mdadm-ing USB drives as long as _they're all_ USB drives? 



2.  Once mounted, the drives are **constantly, rhythmically active**. Like a heartbeat of armatures about once per second. Nothing that I'm running in userspace is accessing them. Nothing that I have touched with my knowlege elsewhere is. After a reboot and prior to mounting the md, they are inactive and quiet. 

Ideas as to why? 



3.  The individual drive UUIDs (from [FONT=Courier New]gdisk -l[/FONT]) of the drives change across reboots (thankfully the array UUID does not). I'll be operating this computer remotely and it's very important that if a drive dies that I can have the person present identify the failed drive to remove it. Changing UUIDs across reboots makes it extremely difficult to identify drives over the phone... 

I'm wondering if maybe I partition the drives prior to raiding them might eliminate this issue? Ideas? 



Anyway, fun times. Many thanks to anybody that made it this far. No, I don't have a soundcloud.

---

### Post by bobnn on 2020-05-04
I had the md127 thing happening to me.  

This was with internal drives, RAID1, under Ubuntu 14.04, back in 2017, but it may still apply.

I found one or more pages on the web advising this:

The first thing was to make the ARRAY lines in mdadm.conf as simple as possible, so it looks lke this:

```
ARRAY /dev/md1 UUID=fdbdfbc1:57d53064:9a2e1ca7:69527446
```

Then, I think it was necessary to run update-initramfs.

I just looked and  found a page addressing this at [https://www.linuxquestions.org/questions/linux-newbie-8/issues-with-raid-creating-as-dev-md127-instead-of-what%27s-in-the-config-4175541446/](https://www.linuxquestions.org/questions/linux-newbie-8/issues-with-raid-creating-as-dev-md127-instead-of-what%27s-in-the-config-4175541446/)  

That pages seems to have it all, while linking to [http://unix.stackexchange.com/questions/71203/ubuntu-how-do-the-md-devices-get-assembled-at-bootup](http://unix.stackexchange.com/questions/71203/ubuntu-how-do-the-md-devices-get-assembled-at-bootup) for more detail on the update-initramfs part.

Also found this in my old browser history: [https://ubuntuforums.org/showthread.php?t=1764861](https://ubuntuforums.org/showthread.php?t=1764861)


I have no idea what's making the "heartbeat of armatures" thing happen, I never had that going on in Linux.  I suppose you've looked at iotop?

---

### Post by sideburnie on 2020-05-04
update: I decided to just label drives with serial numbers from `lshw -class disk -class storage`. I `sudo mdadm --stop /dev/md127`. I remove one drive at a time, look at what changed from `lsblk` and write a serial number on the drive I unplugged. I noticed when I was all finished and all drives were back up, that mdadm had started a 6/4 degraded /dev/md1.... Somewhat strangely I didn't even have it defined in /etc/mdadm/mdadm.conf, but maybe it was cached? Not sure what to take from that. 

Going to try partitioning drives before raiding (sda1, sb1... instead of sda, sdb...) this time. hoping maybe UUIDs remain?

---

### Post by sideburnie on 2020-05-04
posted before a refresh! thanks @bobnn! 

Yeah, iotop showed no meaningful activity. I hadn't been running update-initramfs because it's not a boot drive, but maybe I should be doing it even for non boot drives. Time for more reading and learnin! Looks like it solved several other people's issue. 

I'll try the simpler array definition also as soon as the rebuild is finished.

---

### Post by bobnn on 2020-05-04
Hmmm, my RAID *was* the drive I was booting from......   Anyhow, good luck.

---

### Post by bobnn on 2020-05-05
> **sideburnie said:**
> Going to try partitioning drives before raiding (sda1, sb1... instead of sda, sdb...) this time. hoping maybe UUIDs remain?

I wasn't trying to RAID whole disks, so I had to partition. When doing that, there is a specific partition type for RAID, so this probably wouldn't hurt.

---

### Post by sideburnie on 2020-05-05
`[FONT=Courier New]update-initramfs -u[/FONT]` worked! The array now persists as [FONT=Courier New]/dev/md1[/FONT] across reboots. Thanks @bobnn! 

Partitioning before raiding did in fact make UUIDs persist across reboots, even after removing and re-adding a drive from the array! Success! 

There was so little activity from [FONT=Courier New]iotop[/FONT] last time that I missed the few kilobytes per second of [FONT=Courier New]ext4lazyinit[/FONT]. Wondering if that's my rhythmic drive accessing. It didn't seem to go away after a couple days last time, but I wonder if maybe it needs even more than that... 

Something else I learned! 

4.  When I unplug a drive, re-plug, and [FONT=Courier New]sudo mdadm /dev/md1 --re-add /dev/sdh1[/FONT] *while the md1 filesystem is unmounted*, the raid comes right into consistency as [FONT=Courier New]active[/FONT]. If I do the same *while md1 is mounted* mdadm will start a (very lengthy) rebuild. I've done no writing to the filesystem in between power up and power down in either case. But I'm realizing that maybe [FONT=Courier New]ext4lazyinit[/FONT] was doing the writing and making [FONT=Courier New]mdadm[/FONT] think the array had gone out of consistency. To avoid the lengthy rebuild, I had tried just rebooting, and mdadm brought the array right back up as [FONT=Courier New]active[/FONT] without any rebuilding. 

This time, instead of rebooting, I tried unmounting [FONT=Courier New]md1[/FONT] before [FONT=Courier New]sudo mdadm /dev/md1 --re-add /dev/sdh1[/FONT]. The re-add triggered a rebuild, but the rebuild was finished almost immediately. I think I might actually have something close to workable now... I guess time will tell how often a USB device gets kicked out for some reason and forces me to unmount and do a rebuild.... 

Anybody else here have good / bad experiences to report doing raids over USB over extended periods? If so, any tips?

---

### Post by TheFu on 2020-05-05
I want all external disk connectors to have screws.  I've seen too many flaky USB connections AND a few internal SATA (straight, not 90deg) cables come loose over the decades.  The first USB3 controllers had some issues with disk queuing which made using USB to run an OS problematic.  Seems that may have been solved, but I do have a box here from 2010 that still has the queuing issue for any USB connections.

All new storage using LVM and LVM RAID, not mdadm here.  As long as we are going to the effort, might as well get the flexibility that LVM provides AND avoid having 2 tools involved.  Remember reading somewhere that the LVM guys stole the mdadm software for RAID and striping, but I've also see some performance stats that show RAID10 with mdadm to be 3% faster than RAID10 with LVM RAID10.  I'm not a fan of RAID3,4,5,6.  Just RAID1, and RAID10.  To each their own.  Still have a few RAID1 arrays here, but we consider them legacy.

---

