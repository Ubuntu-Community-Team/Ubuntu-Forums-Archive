---
title: "ZFS best option for keeping data safe?"
date: 2015-05-03
forum: General Help
---

### Post by pantera989 on 2015-05-03
I'm currently building a second computer to use for file storage, and eventually to host other items as well (web sites etc). Going to be using Ubuntu as it's an OS I'm somewhat familiar with and because options like FreeNAS, which would probably suit me better for my storage needs, won't allow me to do much else. I'm trying to store two main sets of data, low importance files like movies, that can be replaced (although would be a pain), and backups of critical data from my main computer (Windows 10)

I have a few questions:

1, is ZFS the best option for keeping data safe on Ubuntu? (Probably using the RAIDZ1)
2. Does RAIDZ1 have all the shortcomings of RAID5?
3, Is there a better option for adding some amount resiliency against failed drives and data rot, while retaining good disk space efficiency, for example, raid 10 half's my disk space, essentially doubling my HDD cost, and trying to keep to a small form factor, more drives means a bigger case.
4. Does anyone have any favourite guides for settings up ZFS/RAIDZ1 on Ubuntu, currently I've been looking at: [http://arstechnica.com/information-technology/2014/02/23/ars-walkthrough-using-the-zfs-next-gen-filesystem-on-linux/](http://arstechnica.com/information-technology/2014/02/23/ars-walkthrough-using-the-zfs-next-gen-filesystem-on-linux/)

---

### Post by TheFu on 2015-05-04
Backups are the best option for keeping data safe by 1000x.  NOTHING replaces having backups and multiple backups for anything critical.

Everyone I know uses RAIDz2, not RAIDz. They go with RAID6 before RAIDz.

ZFS is RAM and CPU hungry.  The general recommendation is 1G of RAM for every 2TB of storage with 8G min RAM. More if you run de-dup. Some people do run with less RAM and think the performance is fine. I've read that on these forums, but all the people I know personally disagree.

RAID is about HA, not data recovery.  If you can live with 12 hrs of downtime, don't bother with RAID-anything.  I'd rather see you get solid, know-you-can-restore-backups working first. You need those anyway.

For things that change daily, use daily backups, automatic, rdiff-backup.  That's documents, emails, code repos (git, cvs, svn), system settings, system DevOps files (ansible/puppet/chef/rexify) - small files.

For media files that don't change much, if ever, I use rsync.  That's music, audio, videos, ISOs, reference VM image files. These are mirrored as needed, but usually weekly.

The RAID arrays in use here are NOT for media files. They are for running business virtual machines. We use SW RAID1.  I've run SW-RAID5, HW-RAID1/5 and ZFS previously as a learning exercise.  The HW-RAID card failed and I was unable to get an exact replacement, so that data was gone. Thankfully, I had a backup.  For ZFS, the performance sucked and I was unwilling to throw 16-32G of RAM at a server just for storage. RAID5 write performance sucked using mdadm and it didn't meet the performance requirements. RAID1 with mdadm does.  The RAID5 "shortcomings" are mitigated by 1) having a UPS and 2) having backups, but that doesn't help performance. Only HW-RAID solves that, I'm afraid. Buy 2 identical quality HW-RAID cards - probably LSI models for $350+/ea if you need that.  The so-called "write hole" in RAID5 is extremely unlikely. I've never seen it.

I'm not anti-RAIDz2 at all.  Just be prepared that there is a cost in complexity and hardware.  FreeNAS isn't THAT limiting. I thought most people had switched to a fork of the FreeNAS project anyway - still has the same issues, but will happily run lots of popular 24/7 home servers like plex, bt, and all the video pirate things the kids seem to like these days.

IMHO. Hope this helps.  Look forward to seeing different options.

Oh ... and I couldn't stop laughing when you said that you had "critical data" on a Win10 computer. Thanks, I needed that this morning. You realize that OS is a "tech preview", right?  If you are serious, you and I have extremely different ideas of "critical data" and you should probably ignore everything written above. 

Heck, I didn't switch to EXT4 until about a year ago because the file system was untested in my mind with only 5 yrs of real-world use.  Data is more important than anything else inside a data center. If I have offsite backups and the data center burns to the ground, it is an inconvenience, but the company will continue.  If the data is gone, we're screwed and need to close the company down. It is that simple.  We primarily used JFS before that and never lost a bit except due to human error. Sure, there were a few trial pockets with ext2 and ext3, but the "critical data" was on JFS storage.  ZFS on a 64-bit Linux doesn't scare me today, but it does on 32-bit and it did until about 2 yrs ago. Unproven.

IMHO.

---

