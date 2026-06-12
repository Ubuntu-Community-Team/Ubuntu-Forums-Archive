---
title: "System dosn't boot after shrinking image"
date: 2020-09-06
forum: General Help
---

### Post by tsumitsuki on 2020-09-06
I converted my physical[COLOR=#000000][FONT=&amp] Ubuntu 18.04 server [/FONT][/COLOR]maschine into an image running on unRaid.


Cause the image is 1TB (size of the original HDD) and the data itself is just about 170GB, i shrinked the main partition vda2 with gparted to 200GB.


At this Point the vm is running fine.
But the image is still 1TB with about 800GB unpartitioned wasted space.


I followed Spaceinvader Ones [Tutorial]("https://www.youtube.com/watch?v=wJBrEoq8mHo") to shrink the image down to 250GB via qemus resize command. Just to leave some spare and increacing the partition later to the full 250GB.


But after shrinking the the image to 250GB the vm dosn't boot anymore.
[https://imgur.com/a/EJH53xc](https://imgur.com/a/EJH53xc)


Since two month now i'm stuck here. Tryed several things but nothing workted or broke it even more. (I have backups!)
e.g. this one: [Link]("https://www.linuxmintusers.de/index.php?topic=42844.msg610268#msg610268") [German Mint Forum]




I've 1TB left on the HDD, but it would be great to move it to an fast SSD to increase the performance since the vm is running a gameserver. And 1TB SSDs are not cheap (not for me). And even with the normal HDD it's a waste of storage-space.

---

### Post by TheFu on 2020-09-08
If it were me, I'd create fresh storage of the size needed, then use fsarchiver to clone each partition, then fix the changes required in the fstab. fsarchiver understands many file systems, so restoring to a smaller location works.  If you can have both storage areas connected at the same time, you could also use a live-try-ubuntu environment with the old and new storage, then use rsync to mirror all the files over.  This assumes you fully understand Unix permissions and how to use rsync correctly to maintain that stuff.

Reputable tutorials are hard to find. Often, people really new to Linux and storage management think they fully understand things when they don't, but that doesn't stop them from being excited to show something that worked for them.

---

