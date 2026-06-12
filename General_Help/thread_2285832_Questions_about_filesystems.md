---
title: "Questions about filesystems"
date: 2015-07-08
forum: General Help
---

### Post by temroa on 2015-07-08
1.which fs is most reliable for  /home directory
2.if im a notebook user and i want to use btrfs for /home which mount options are power related also which options i should turn on or off
3.when installing ubuntu 14.04.2
How can i choose and use reiser4 for /var?

---

### Post by tgalati4 on 2015-07-08
Welcome to the forums.  I would use Ext4 for both /home and /var.  Reiser4 is not supported (to my knowledge), as the principal developer is in prison--which makes for interesting reading, but not sure if its performance is better than btrfs.  For a notebook, you want journaling and there are no features that you should turn off, since all of those features contribute to reliability.  Unless you are running strickly in RAM and back up your data (hourly) to a USB stick, I would stick with Ext4 for simplicity and reliability.

What is your Use Case that calls for btrfs for /home and reiser4 for /var?

---

### Post by TheFu on 2015-07-08
No file system is 100% reliable.  That is why people make backups - versioned backups are important.

btrfs has known performance issues for virtual machines (the KVM wiki explains) and is too new to be completely trusted, IMHO. If you go this way, having backups is absolutely critical.  If you do - thanks for being a beta tester.  For /home, with a normal situation, I'd use ext4 today using LVM so snapshots and resizing of the LV becomes a minor issue, not a reboot-required event.

There are multiple ways to accomplish what you want for /var.  You can "do something else" during the storage setup while installing, you can use LVM, setup VGs, LVs and make /var with mkfs -t reiser or you can fix it after the fact.  

I just did this for fun last week - the var directory was on / partition, but I needed to move it to a dedicated partition.  I use LVM and always leave room to add or provide space for new LVs inside the main VG.  To make it happen quickly, I wrote a little script to sync the existing data from var to a temporary mount storage.  Of course, did all of this from single-user mode. It wasn't really for fun - more as an training exercise.

If I were really nervous, I'd have done it from a live-Boot ISO.  That's another way.

As you know, different file systems have different purposes.  There are all sorts of reasons to use each one based on the total data, how many users, how large files might be, total throughput, deduplication, snapshot support and strong parity validation needs. Oh - if the file system is SSD or spinning matters too. The more file systems used, the larger the memory requirements too. That is also a consideration for some environments. Each option is a trade-off.

---

