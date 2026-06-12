---
title: "Raid 1 failures"
date: 2013-05-02
forum: General Help
---

### Post by tobiz on 2013-05-02
I'm running ubuntu 11.10 with the main boot partition and s/w on an SSD and a RAID 1 partition setup for holding all my mythtv recordings.  The server is set to auto-start when there is a recording to be made.  Problem is that sometimes (and only sometimes) the system doesn't boot it just stops at a point where it requests which OS to use (no good when there's no one around!!)  Normally hitting return on the default ubuntu version selected results in the system completing startup.  My past investigations suggested that the failure is due to the RAID 1 partition not coming up, I've seen, for example, the situation where the array only has one disc and needs the other to be recovered (which being 1TB can take some time), even then a re-boot can sometimes resolve this straight away.  The system not fully starting seems to be random and seems to be related to the RAID 1 array failing to start.  I think I've seen it mentioned that this is a known problem with Linux RAID, however, any ideas as to what might be causing the problem and/or how to fix it would be welcome as I'd like this system to become my operational one replacing my ageing 8.10 mythtv system, at the moment this can't happen as it's too unreliable.

---

### Post by TheFu on 2013-05-02
Check the cables.  I had a similar issue and it was a loose SATA cable. The vibration from the fans in the array loosened the connection over time. I ended up switching to 90 deg SATA cables and the issue was solved. That was 5+ yrs ago. No problem since.

Also, I'd strongly suggest migrating to 12.04 - an LTS supported release.  If your other machines connect to the internet at all, there is a risk of being hacked on those non-maintained releases.  You know this already, I'm certain.

---

### Post by tobiz on 2013-05-02
> **TheFu said:**
> Check the cables.  I had a similar issue and it was a loose SATA cable. The vibration from the fans in the array loosened the connection over time. I ended up switching to 90 deg SATA cables and the issue was solved. That was 5+ yrs ago. No problem since.

Also, I'd strongly suggest migrating to 12.04 - an LTS supported release.  If your other machines connect to the internet at all, there is a risk of being hacked on those non-maintained releases.  You know this already, I'm certain.

Thanks TheFu, some interesting ideas there I'd not thought of; I'll try the cable idea. Re upgrading to 12.04 I always keep my ubuntu releases up to date as and when revisions are issued which are mostly security ones. Re upgrading to 12.04 I might consider that just so as to be more 'up to date' but not so keen on the loss of gnome 2.

---

### Post by TheFu on 2013-05-02
11.10  hasn't been supported in a few years, so any "updates" you may have been running haven't actually done anything.  12.04 gets 5 years of patches.  The non-LTS releases like 11.10, 12.10, 13.04 get patches for about a year ... about 9 months in reality.  Unless you are willing to migrate from release to release every 6 months or so, an LTS release is the best choice, IMHO.

---

### Post by tobiz on 2013-05-03
Irrespective of the LTS issue I've discovered that one of the discs is failing, in fact it failed some time ago.  Looking at the log I found:

Apr  8 21:02:28 mms2 kernel: [  311.812253] md/raid1:md0: Disk failure on sdb1, disabling device.
Apr  8 21:02:28 mms2 kernel: [  311.812258] md/raid1:md0: Operation continuing on 1 devices.
Apr 10 19:57:32 mms2 kernel: [    5.963428] md/raid1:md0: active with 1 out of 2 mirrors

From then on the system runs on 1 disc.  It seems the issue is the disc failing and, then failing to boot due to this eventually, for some unknown reason. Connecting the disc back into the array has started recovery.  After that I'll try and test the disc.  I'll then look into a script to attempt auto-recovery as it always seems to work.

---

### Post by TheFu on 2013-05-03
I get emails from the system when any RAID fails.
Another option is to install something like logwatch - which will let you know about failures.

**badblocks** is a good tool to check a disk. SMART data is only useful if you watch the data change over time.  I would do this on a different machine by moving the HDD over and running these tools after replacing the suspected bad HDD with a new one.  After all, your data was important enough to RAID.

---

### Post by tobiz on 2014-01-27
I abandoned this RAID set up since in the end I discovered it was the WD Red 1TB discs causing the problems.  I got one replaced under the RMA scheme and bought 2 Samsung 1TB HDDs.  I then used zfs for a RAID 1 set up with 1xWD and 1xSamsung HDD.  This ran ok for a while until the WD failed! Using zfs it was simple to replace the WD Red disc with another Samsung HDD, ever since then there have been no problems.  Moral to the story, WD Red 1TB seem to have reliability problems, zfs is the way to go for RAID.

---

