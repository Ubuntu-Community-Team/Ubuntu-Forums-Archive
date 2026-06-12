---
title: "Ubuntu 14.04 with full system encryption - Backup to USB?"
date: 2014-05-30
forum: General Help
---

### Post by Jaman42 on 2014-05-30
Hi,
I have a device that runs Ubuntu 14.04 with full system encryption on a 180GB SSD, I want to backup (clone) the disk to a USB connected SSD on a regular basis. The intention is to get a exact replicate so I could just switch the disks in case of internal disk failure. 

Is this possible to do on a schedule without rebooting the unit?

The idea is like I already said to get a identical backup disk for quick switch. Any other ways of doing it? Will the backup also be encrypted?

Thanks for reading

---

### Post by TheFu on 2014-05-31
Backing up actively used files on a running system is dangerous. With encryption, it is even more dangerous.  Can it be done? Yes. Is it guaranteed to be useful, non-corrupted, after, NOPE!  I wouldn't do it.

The type of whole drive encryption matters too.  Is this in-hardware encryption? Then it is doubtful the USB port supports the command set necessary for encryption.  Please be extremely specific on the encryption used.  Also, no that there are successful attacks against Linux whole drive encryption - google a little for examples - the defcon guys are really smart. Physical access means ownership, eventually.

If you want to clone the data on any partition, do that by booting off different media.  That media can be a tiny partition on the same HDD or anywhere else you can boot.

Is there a better way?  For certain values of "better", most certainly, but probably NOT for what your end goal is.  I would suggest that monthly cloning is probably enough, then use normal daily backup methods to handle everything else from an incremental perspective. My incremental backups take between 20 seconds and 4 minutes across the 30 systems here.  I cannot just swap drives for the restore, but a full restore to any point in the last 30-120 days (different systems have different backup retention) takes less than 1 hr. If 1 hr is acceptable as an RTO (look it up to open a completely new world), then perhaps cloning a HDD just isn't needed?

If I need greater uptime, then running in RAID1 or RAID10 mode is necessary. RAID is for HA, but definitely do not replace backups.

---

### Post by Jaman42 on 2014-06-03
Thank you for the insight, I will do full system backups manually now and then and backup important files on a schedule.

---

### Post by HermanAB on 2014-06-03
Another reason cloning disks don't work, is because the UUIDs of the two disks will be different.

Just backup your data.  Saving the whole bladdy system is just a waste of good bits.  One day when your system croaks, you will want the latest and greatest Ubuntu system anyway and not an old tired backup.

---

### Post by TheFu on 2014-06-03
If he clones the entire HDD, then the labels should be identical, mounting by-label can get around that concern ... though I don't know if it works well for encrypted drives.  I suspect that would matter completely on the type of encryption used.

In the last few weekends, I helped someone relatively new to linux at my local LUG create a daily backup script for his system that got all the important data needed to restore a system to be 99.9999% the same after a restore as before.  Plus it didn't backup the 4G of OS files, just the critical settings, list of installed packages and his data, settings and specially installed programs (outside the package manager).  Perfect. Automatic via anacron (/etc/cron.daily ) and extremely storage efficient.  I need to make a presentation about this method.  It is great for migrating between systems too - same OS, different release, as long as they are in the same "OS family", it should be fine.

---

### Post by sudodus on 2014-06-03
The UUIDs of the partitions will be cloned. Also the UUID of the drive will be cloned. I'm talking about what is shown for example by

```
sudo fdisk -lu|grep 'Disk identifier'
```

(in English, grep the relevant phrase in another language) for an MSDOS partition table. You can check for a GPT too, by for example

```
sudo gdisk -l /dev/sdc|grep 'Disk identifier'
```

I know that most systems work when cloned into another drive. It  is not too hard to check it for Ubuntu 14.04 with full system encryption  (for example using two USB pendrives and cloning from the smaller one  to the bigger one).

I think it works, but ***you should check it yourself, if you want to be sure that it works for you*** with full system encryption.

*Edit*: Cloning should be done between drives without any partitions mounted. So you should boot from a third drive. And it is risky, at least if you use dd. (Cloning with Clonezilla should be safer, but I doubt it would work in this case.) It is extremely important that you identify your drives correctly (for example by size), otherwise you can easily restore instead of backup (and overwrite what you wanted to backup).

The best alternative would be to use a shell-script, that is identifying the drives in a correct way and runs the cloning command.

---

