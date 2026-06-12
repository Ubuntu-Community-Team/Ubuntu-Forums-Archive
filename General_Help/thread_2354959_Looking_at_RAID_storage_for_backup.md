---
title: "Looking at RAID storage for backup"
date: 2017-03-08
forum: General Help
---

### Post by david_brown on 2017-03-08
I have a server running Ubuntu 16.04 and am looking to expand the storage. It is used as a Plex server basically.

Currently I have a WD red 3TB as main storage and a WD red 2TB + usb 1TB as backups. Backup is done by running cron jobs. I'm thinking of getting another 3TB WD red to give a total of 8TB in the box, getting a raid card to run them.

Confession - I'm a complete RAID newbie and have only just started looking into it so would like some advice. Specifically, given the non matching drive sizes, what raid would be best for me? I'd like it so that if one drive goes down there remains a complete data set. Also, recommendations for cheap raid cards and any general advice on what I'm looking at doing is appreciated.

Thanks

---

### Post by mastablasta on 2017-03-08
1. RAID is not a backup. RAID is disk redundancy. in other words if one disk goes down the server keeps on working. if you get corrupted data on one disk that is then mirrored on the other.
for backup you actually need versioned backups on another disk. which should be bighger than the first disk. another option might be BTRFS or ZFS with RAID mirror. this could make snapshots.


2. you do not need a RAID card as you can use mdadm to setup software RAID which is a better solution.

3. get 2 disks of same size and do RAID1. but before you do see item 1.

---

### Post by gordintoronto on 2017-03-08
And if you accidentally delete a file, RAID will not help you recover it.

---

### Post by DuckHook on 2017-03-08
For general users, RAID actually makes your system more fragile; not less. All you have to do is search through old threads on these forums to see people stuck because of broken mirrors, corrupted arrays and borked migrations/upgrades.

As both mastablasta and gordintoronto have implied, RAID is usually misapplied and unnecessary for general use (and this includes Plex). It is basically enterprise-level technology for people who simply cannot afford to be down for even one second. It requires constant oversight and nannying. I would not recommend it for SOHO use.

If you wish to mirror your data for redundancy (which still does not constitute backing up), a better strategy is to source a cheap second computer and sync to your main box using rsync. If you follow proper Linux server protocol and don't install a GUI, any old desktop with a big HDD will do. You could do it for less than $200. This strategy has the advantage of giving you a completely separate second machine in case your main box dies of non-HDD causes. Consider the pickle you would be in using your RAID strategy if it's your MOBO or PSU that breaks.

You could also use the second box for a proper backup strategy involving removable drives, and proper versioned backups or rotating full syncs. I use the latter strategy because USB HDDs have come down in price so much these days that I can rotate four 2TB HDDs weekly (which gives me a monthly rotation schedule) for less than $200.

---

### Post by david_brown on 2017-03-10
Thanks for the replies. I think the answer is to buy another drive for expansion and jiggle where I store and back up data to so that storage and backup is equal. I'll continue with the cron jobs for backup.

---

### Post by ltburch2000 on 2017-03-10
Storage is relatively cheap, and drives always fail eventually.  RAID (MDADM),  as far as storage (not main  drive) has been pretty well supported for a long time now.  There is no need to resort to using a separate machine and relying upon (talk about fragile) rsync scripts to keep things going.  If you loose a PSU or a MB, replace it, or just yank the drives out and plug them into another machine.

RAID isn't a backup it is true, but given the state of home backup devices, it is both difficult and time consuming to backup large amounts of data (such  as media) which if push came to shove could probably be replaced.  For something more precious and potentially irreplaceable, you are probably better off with a cloud based backup, that way, come fire, flood or other natural disaster recovery is still possible.

---

