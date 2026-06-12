---
title: "Data integrity"
date: 2008-01-05
forum: General Help
---

### Post by isaacjoe on 2008-01-05
I've been having a problem with large files losing their integrity. I've been downloading lots of ~300 meg AVI files from my university's file sharing network, and a good portion of the video files are just corrupted enough to become unreadable to VLC or any other software a few minutes into playing the file. When I transfer known-good video files from my other computer to this one across the network, I have the same problem. When I try to download torrents, the torrent software will usually report disk errors on larger files. I don't encounter any of these problems on my other computer.

These signs all indicate to me that my drive may be failing, so I would like to know the best way to thoroughly test my drive to figure out what, if anything, is wrong with it. I've shrank the partitions and installed Ubuntu, then deleted all the partitions and did a fresh install of Windows XP/ Ubuntu a year later, wondering if that makes my drive wear faster? 

Thanks,
 Isaacjoe

---

### Post by frankos44 on 2008-01-05
You could try checking out your RAM. Ubuntu has an option on the CD todo this.

---

### Post by isaacjoe on 2008-01-05
> **frankos44 said:**
> You could try checking out your RAM. Ubuntu has an option on the CD todo this.

The memory tester in the GRUB boot menu? I'll give that a go and post back.

---

### Post by isaacjoe on 2008-01-05
Memtest 86 reported no errors, still looking for ways to test my drive.

---

### Post by articpenguin on 2008-01-05
what file system are you using? if your using ext3 try using jfs. JFS does a lot better at large files then ext3. if jfs does the same thing  then your drive might be failing

---

### Post by isaacjoe on 2008-01-21
I experience massive slowdown issues when I use file sharing programs in both windows (ntfs) and ubuntu (ext3), big files that I copy frequently have issues. I've dropped the laptop a few times and moved it around frequently while the disk is running. What I want to do is run some kind of scanning program that can tell me BANG my drive is good or BANG it's bad, because I'm a poor college student and can't afford to just buy a new hard drive because I *think* my drive is bad.

Does something like that exist, because I haven't been able to find anything. This is a hardware question, I'm pretty certain

---

### Post by articpenguin on 2008-01-23
> **isaacjoe said:**
> I experience massive slowdown issues when I use file sharing programs in both windows (ntfs) and ubuntu (ext3), big files that I copy frequently have issues. I've dropped the laptop a few times and moved it around frequently while the disk is running. What I want to do is run some kind of scanning program that can tell me BANG my drive is good or BANG it's bad, because I'm a poor college student and can't afford to just buy a new hard drive because I *think* my drive is bad.

Does something like that exist, because I haven't been able to find anything. This is a hardware question, I'm pretty certain

if the hard disk is running now i think it is fine.

---

