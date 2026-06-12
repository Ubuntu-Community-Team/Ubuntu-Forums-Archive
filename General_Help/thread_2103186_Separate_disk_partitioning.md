---
title: "Separate disk partitioning"
date: 2013-01-09
forum: General Help
---

### Post by johnlugh on 2013-01-09
I currently have 2 hard drives installed, recently adding a 2tb one purely for added storage. 

As it happens, now I run dual boot with both the root partition and windows on one hard drive, with the 2nd drive being dedicated to the home partition. 

As I don't use windows very much and the root partition doesn't need much space, is there a way I can utilise the free space on one drive so I can have more storage for my home folder? I've searched for solutions but can't seem to find anything specific to my needs...

Thanks.

---

### Post by SlugSlug on 2013-01-09
I think LVM might be able to help there if it's a separate partition.

But tbh I'd just mount it as a folder in your home

eg

/home/user/Music

and just keep your Music on that partition

---

### Post by Wim Sturkenboom on 2013-01-09
I have a 1TB hard disk for photos. I've mounted it on /mnt/photos (using a line in /etc/fstab). And I've placed a shortcut on my desktop for it (or you can use SlugSlug's suggestion to mount it somewhere in your home directory)

You can call it multimedia if you feel like that and store all multimedia stuff on it.

---

