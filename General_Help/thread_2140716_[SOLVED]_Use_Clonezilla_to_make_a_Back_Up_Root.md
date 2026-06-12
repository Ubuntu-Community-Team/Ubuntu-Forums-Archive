---
title: "[SOLVED] Use Clonezilla to make a Back Up Root"
date: 2013-04-30
forum: General Help
---

### Post by wannabegeek on 2013-04-30
Hi all...

I'm using an SSD ( sda ) for my /home and / directories and keep a large spinning iron HD ( sdb ) for various other files. I also 
keep a copy of my /home on sdb as an on-the-road backup in case  my SSD fails.

I kept my old root on the spinning drive ( sdb ) and thought it may come in handy if the SSD failed...
I also used Clonezilla to make a clone of my SSD drive that lives on an external backup drive.

I'd like to update this arrangement, so that I have a clone of my SSD drive on my spinning iron, so that 
if the SSD failed, I'd just switch to sbd to boot.

My question is, can I use the Clonezilla img to make the clone on  sdb ...? Is there anything I should be careful of...?


I hope that I've explained this properly...

TIA!
wbg

---

### Post by oldfred on 2013-04-30
You cannot have an exact clone with both drives mounted.
Exact clone with have same UUID for partitions and system cannot have duplicates. 
You have to change UUIDs, reinstall grub, and edit fstab with new UUID. And then you cannot copy any of those settings, so it never is exactly the same.

I prefer just to do another install & copy /home settings with rsync (with settings) or cp -a to preserve ownership & permissions. All the user settings are in /home. If you have installed a lot of applications you can reinstall with dpkg or if not houselcleaned in SSD copy downloads.
 Location of downloaded debs
/var/cache/apt/archives/

---

### Post by wannabegeek on 2013-04-30
Thanks that's good advice and clears up part of my confusion...

It's usually just easier to go through installation isn't it...? It's more of an emergency setup than any too...

I'm going to be on the road interviewing and if my SSD crashed I'd be damned happy to have a basic installation on my iron
with a copy of the SSD's home...

Cheers !

My task for tomorrow is set...unemployment sux...

---

