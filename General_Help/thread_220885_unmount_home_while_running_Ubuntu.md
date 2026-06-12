---
title: "unmount /home while running Ubuntu?"
date: 2006-07-22
forum: General Help
---

### Post by nickbaker77 on 2006-07-22
Hi all,

Probably a dumb-*** linux question here, but can you unmount /home while using Ubuntu (not Live)?

The reason I ask is that I want to split my /home partition into 2 parts, one of which I want to reformat as NTFS (I have dual boot with XP and am running out of space in XP). This is actually to store my music in, so if there's a way of storing the MP3s in a partition that can be shared by XP/Ubuntu that would be even better...

The reason I'm not using GPartiton from Ubuntu Live is that my CD drive seems to have packed up!

Cheers

Nick

---

### Post by ajgreeny on 2006-07-22
The easiest way would be to make a new shared partition as a fat32 file type which is read/write capable by both winXP and Ubuntu.  Having made the partition you would then need to mount it as /home in your Ubuntu installation and copy all your home files over to it.  I am certain there is a wiki or something similar if you search for it which will give you more details of how to proceed.

---

### Post by ifokkema on 2006-07-23
> **nickbaker77 said:**
> (...) but can you unmount /home while using Ubuntu (not Live)?
You could, if you make sure you don't use files there (don't log in using your username). If you don't have a root account (which is the default), reboot in recovery mode.

> **nickbaker77 said:**
> (...) so if there's a way of storing the MP3s in a partition that can be shared by XP/Ubuntu that would be even better...
If you have unpartitioned space left... that's an easy thing to do.

> **nickbaker77 said:**
> The reason I'm not using GPartiton from Ubuntu Live is that my CD drive seems to have packed up!
You can download and install it from the repositories as well!

---

