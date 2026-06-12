---
title: "Amarok keeps forgetting its collection"
date: 2008-03-17
forum: General Help
---

### Post by Xianath on 2008-03-17
Hi all,

I've searched the forums and Google but found no definite answer to my problem, hence I decided to ask in hope of help.

My music collection is stored on an external USB HDD formatted with NTFS under Ubuntu. I mount it manually (no sudo -- I've suid'ed fuser, fusermount and ntfs-3g and have allowother in fstab) and have no problems accessing it. However Amarok keeps forgetting its collection. I tried all three collection backends and the result is the same. When I check the respective backend database I see the entries are in there, but Amarok still insists on rebuilding the collection almost (!) every time the disk is mounted. This takes 30-60 min of heavy HDD and CPU usage every day and is therefore quite unacceptable. Is there anything I am missing?

This is Ubuntu Feisty Fawn i386, up-to-date.

Thanks,
Peter

---

### Post by monsters on 2008-03-17
I have the same situation, it's forced me to use rhythmBox instead.

---

### Post by _eti_ on 2008-03-20
Hi, i can confirm Xianath's problem. The only difference is that i have a USB Disk with fat32 format.
I was looking on the web, launchpad etc. but also couln't find any hint. 
Amarok forgets the collection most of the time after shutdown, reboot or suspend. I think it has somthing to do with de mountpoint (/media: disk or disk-1) even tougt the settings in Amarok are still correct.
By the way, it also happens in Gutsy and Hardy.

Thanks,
Eti

edit:
Sorry to have posted it on the stable forum...
Meanwhile  the problem is solved in Hardy.

---

