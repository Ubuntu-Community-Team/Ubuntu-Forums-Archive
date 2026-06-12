---
title: "New to ubuntu, have a few questions."
date: 2007-04-17
forum: General Help
---

### Post by DarthZug on 2007-04-17
I'm wanting to use ubuntu as a file server for my home network.  Currently I have a computer running Windows 2003 Server 64-bit.  It has over 2TB of storage on it.  I'm going to be using MythTV and wanted to setup this server as the backend box since is has all the storage.  

My questions are what is a good Newsgroup Reader, DVD Ripping, DVD Shrinking, and DVD Burning programs for Linux.  As these are task that are done on this server.  And how good it ubuntu at managing several hard disk?  My server has about 8-9 disk, both SATA and IDE.

---

### Post by jakev383 on 2007-04-17
For DVD ripping and shrinking, you can look at k9copy or xdvdshrink. I think they're both in Synaptic if you enable the multiverse and backports. I have not tried them myself.
How does it handle drives? I have a similar machine to yours. 2TB total, 12 drives total (1 boot/OS HD, 1 CD-Burner). 10 of those drives are plugged into IDE cards I installed and all in a RAID5 array. Never, and I repeat, NEVER had a problem with this machine in 2 years. I used good hardware to begin with (Intel motherboard, Intel P4, Seagate drives) and this machine has never had a hiccup. All of my drives are ATA so I never mixed SATA's in there (IDE's were just too cheap at the time), so your mileage may vary on that one. But I suspect you won't have any issues if the hardware is good.

---

### Post by FluffyElmo on 2007-04-17
I use *k9copy* for DVD shrinking/copying and *DVD::Rip* for DVD ripping. *k3b* is a good DVD burning tool, if you're looking to make menus there are a number of ways to go about that but it's probably not as easy as Windows. *Pan* is a good newsgroup reader and has good binary support though you'll want the command line tools *par2repair* and *lxsplit* as well.

Note that MythTV itself has a module for ripping DVDs and there are modules available for backing your recordings up to DVD so you may not have as much of a need for specific GUI tools as you think.

---

