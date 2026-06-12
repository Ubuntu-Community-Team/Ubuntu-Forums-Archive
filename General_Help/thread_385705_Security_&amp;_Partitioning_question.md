---
title: "Security &amp; Partitioning question"
date: 2007-03-16
forum: General Help
---

### Post by mmilitia9 on 2007-03-16
I just began reading, "The Unofficial Ubuntu 6.10 starters guide.

and I have 2 questions for you guys..


See, I want to have XP and Ubuntu installed.  I have a lot of documents/files that will open and run within Ubuntu.  I came across this section in the starter guide that said


"Mounting Windows Partition to read/write".  I'm going to assume this is the step I want to take so I don't need to back up any files within Windows and transfer them to Ubuntu(correct me if I'm wrong). I'm taking this action because I don't want to waste HD space by duplicating files.. So is this the right procedure?

I'm also going to assume that the ONLY time I could be able to access those files from XP is when the XP partition is mounted.  So,  Is leaving it mounted 24-7 a bad idea?  Is this safe?  Any performance decreases?


Now,  my question that is security related is..Well, let me start off with saying I understand that Linux is almost completely indestructible if used right. Soo..with that said. If my Windows partition is mounted in order for me to access some files while connected to internet on Ubuntu.. Is my Windows partition vulnerable in anyway to viruses and whatever else out there because I'm not fully booted in XP with a virus scanner running in the background?  I mean, the chances of this happened are slim I guess.. but it's that what if factor I don't want to take. 

[B]
Or..[/B]


Should I just screw what I said above and make like a Fat32 partition or whatever is computable with both OS's and move my files there to share in both OS's?  Is there still a security issue(Like I said above) with sharing a partition with both OS's when one doesn't require much security and the other HAS to have something running in order to remain secure?  



I hope everyone can comprehend.. Thanks for helping!

Dominick

---

### Post by Adramelech on 2007-03-16
You need ntfs-3g to get read write access to you windows partition. ntfs-3g is just out of beta, is stable and you get no data corruption at all, so is safe to use it. Your windows partition mounted on linux can get viruses but only if you run a virus on wine and wine have access to those discs.

So you are pretty safe if you mount you ntfs hard discs using ntfs-3g and go to wine configuration (console wincfg) and uncheck those hard drives on the "drives" tab

---

