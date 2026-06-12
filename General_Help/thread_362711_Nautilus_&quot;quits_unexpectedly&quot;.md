---
title: "Nautilus &quot;quits unexpectedly&quot;"
date: 2007-02-15
forum: General Help
---

### Post by venator260 on 2007-02-15
I did alot of updates and things to my computer on my last boot up of ubuntu. I then booted up WindowsXP and edited the partitions on the drive that Ubuntu is on to make most of it FAT32, so that I can have files that are accessible and writable by both ubuntu and Windows XP. Also, I had what was the NTFS partition mounted. However, it no longer exists.

I booted it up about 10 minutes ago, and I get a box that says "The application 'nautilus' has quit unexpectedly. When I try to open Places>Computer, the same thing happens. 

I think I should mention that I've been using Linux for all of 2 days, so please be detailed with your responses.

Thanks!!!

---

### Post by dcstar on 2007-02-15
> **venator260 said:**
> I did alot of updates and things to my computer on my last boot up of ubuntu. I then booted up WindowsXP and edited the partitions on the drive that Ubuntu is on to make most of it FAT32, so that I can have files that are accessible and writable by both ubuntu and Windows XP. Also, I had what was the NTFS partition mounted. However, it no longer exists.

I booted it up about 10 minutes ago, and I get a box that says "The application 'nautilus' has quit unexpectedly. When I try to open Places>Computer, the same thing happens. 

I think I should mention that I've been using Linux for all of 2 days, so please be detailed with your responses.

Thanks!!!

Altering partitions post-install can change the UUIDs that are used in the /etc/fstab file, which can cause all sorts of issues.

Since you have been using Linux for only two days, I would recommend deleting your current Linux install and start again with a fresh install (and don't change the partitions..........)

---

