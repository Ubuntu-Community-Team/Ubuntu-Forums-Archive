---
title: "How to test if Software RAID 1 is working or not?"
date: 2014-02-02
forum: General Help
---

### Post by sim085 on 2014-02-02
Hello,

I have implemented Software RAID 1. I now am looking how to test if this is working fine or not.
I want to test this now so that if this is not working then I would not get to know this when it is too late.

Is it just a question of pulling power from one of the drives. Would it be a problem after when I connect everything again?

---

### Post by TheFu on 2014-02-02
Yank the SATA cable.
Pull the power.
Do anything to 1 drive that doesn't happen to the other.

Be aware that RAID is NOT a substitute for backups and if something is NOT working with your RAID setup, then a backup may be the only way to recover.

Setting up RAID and backups is only 10% of the work. The real work comes at recovery time - that is the purpose, after all.  read the manual pages for mdadm to learn to recover after a failure and know that resync of data can take a really long time even for a few seconds of disconnection.  **man mdadm** explains a tremendous amount.

---

### Post by sim085 on 2014-02-05
> **TheFu said:**
> know that resync of data can take a really long time even for a few seconds of disconnection.

mmm... so if I disconnect one of the drives, check that I get an error, and then I connect it back in I'll have to resync? Is there a command so that I can check that the size taken of one drive is the same as the size taken on the other drive? Like that at least I will confirm that data is being written on both drives!

I will make sure to take notes on recovery and hope never to need them :)

---

### Post by TheFu on 2014-02-05
> **sim085 said:**
> mmm... so if I disconnect one of the drives, check that I get an error, and then I connect it back in I'll have to resync? Is there a command so that I can check that the size taken of one drive is the same as the size taken on the other drive? Like that at least I will confirm that data is being written on both drives!

I will make sure to take notes on recovery and hope never to need them :)

Yep. If a RAID1 drive drops from the set, then gets reconnected, a resync will occur which can take hours - days.  **more /proc/mdstat**
If you want to see data being written to both drives, any io-monitoring tool should show it. I use **saidar** to get a warm fuzzy, but it isn't much use beyond that.

I took notes during and after setting up my RAID arrays.  Haven't needed more than these the last 8 yrs. Clearly, modify each command for your situation:
```

more /proc/mdstat
sudo mdadm --detail /dev/mdX # See what is up!
sudo mdadm /dev/mdX -a /dev/sdf1   # if 1 disk drops out
sudo mdadm --assemble /dev/mdX -v --force # if the array is migrated to a new box
# RAID Maintenance - run the "check" weekly
echo check > /sys/block/mdX/md/sync_action
echo repair > /sys/block/mdX/md/sync_action
```
These are just the commands not a script. Each has a specific purpose.  Simple stuff for the most part.

---

