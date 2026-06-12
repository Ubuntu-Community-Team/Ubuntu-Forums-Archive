---
title: "Faulty Ubuntu installation trashed NTFS partition"
date: 2006-11-14
forum: General Help
---

### Post by oxboood on 2006-11-14
Alright dont ask how exactly this happened, but my intentions were to take my 200gb NTFS hard drive w/ winXP on it and partion a portion of it for Ubuntu. I tried using Ubuntu live cd's partitioning tool. Apparently I made some bad choices. I did not format my NTFS windows partition, I just shows up as Unknown file system. Windows boot, obviously didnt like this very much so now when I start my computer it says failed to load OS (xp). What can I do to recover my data? perhaps restore the file system to its correct state... has anyone had a similar issue, or have any tips? because I am just sitting in open water here. Im not really sure what to do... anything would help. Thanks:)

---

### Post by x64Jimbo on 2006-11-14
You didn't back up your data before attempting to resize a partition?

---

### Post by Mr.Carramba on 2006-11-15
since u haven rewritten clusters on your HD, you could seeply reinstall XP and install some of the recovery programs:
GetDataBack (god but sloooow...) or even better one [http://www.nucleustechnologies.com/](http://www.nucleustechnologies.com/) (the easyis to use and makes best (?) result I have seen.
unfortunatly I'm linux newbie so I can only help you solve this using XP

---

### Post by Neobuntu on 2006-11-15
Barring any poor install/partitioning choices on your part, I can't help but wonder if your Motherboard and it's BIOS are currently capable of (fully) handling your 200GB hard drive. Did you upgrade to this 200GB and is your computer a few years old?

The reason I'm thinking this is, a 200GB drive will go on about it's merry until it goes over the (about) 130GB limit; on a lot of motherboards. Then it will wrap and WRITE to the beginning of the drive and act as you have described. I'm concerned many an upgrade over the 130GB hard drive limit (about 2001 computers and back) are time bombs waiting to happen. Some BIOS can be updated past this (48bit) limit and some can't (and Win 95/98/ME won't normally). You'd have to add a new (ATA133) controller on the (PCI) bus as one way to remedy this.

This was just a thought, and a warning. I don't know, it fits your scenario but if you haven't upgraded your 200GB drive then look elsewhere.

Oh yeah, forgive me but ALWAYS have two backups of the stuff you just can't live without, even though I've never seen a Linux install that would erase anything, that I didn't confirm. USB Flash drives are under $10 now (for sizable ones) and will fit your most critical stuff. Then it is a simple click and drag affair.

---

