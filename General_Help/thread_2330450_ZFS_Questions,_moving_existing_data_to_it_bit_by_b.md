---
title: "ZFS Questions, moving existing data to it bit by bit"
date: 2016-07-11
forum: General Help
---

### Post by sciphi on 2016-07-11
I've been reading up on ZFS and it seems like a great way to go for reworking my plex media server at home. 

Currently the box has a collection of 4x8TB and 4x4TB drives for the data and and it is setup with half the drives being used for backup using rsync to mirror them every couple of days. 

What I wanted to check was if I understood correctly. 

To convert everything over to a big ZFS raid pool with a high level of parity (I'm still learning RaidZ2 yes?) I can make three of the discs into this (loosing the data on them) and then start copying the data back from the backup drives and adding the backup drives into the new pool one disc at a time as the data is copied off? Till eventually everything is on the new Raid pool. 

I also gather, if a drive dies, I can add a larger drive back in as a replacement and this wont be a problem, the rebuild will take care of this itself? 

My initial plan was to use ZFS with a straight mirror setup like I currently have but reading up the RAID stuff it does has made me think I was being a tad conservative and to maybe be a bit more ambitious. 

Sorry, these are probably dumb questions but I wanted to get this sorted before I took the plunge. 

Also, is it difficult to move to the pool to a new system? I was planning to replace the server at some point but would obviously like to keep the data and transfer it over. 

I have been using Ubuntu for years and have been using Linux in various guises since the 1.2 series kernels (Go Slackware!) , so I am not a complete newbie but I haven't done this before. 

Jason

---

