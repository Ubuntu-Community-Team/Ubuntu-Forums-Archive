---
title: "Problems burning DVDs"
date: 2007-08-01
forum: General Help
---

### Post by jon.reeve on 2007-08-01
Nautilus recognizes my blank DVDs with no problems, but when I press "Write to Disc" and configure the options there, I get a message saying: 

> Please replace the disc in the drive with a supported disc with at least 4.6 GiB free.  The following disc types are supported:

...that is, without any disc types listed. Does this mean I'm missing a library of some sort? Does anyone know how to fix this? 

As far as I can tell, I'm using the right types of DVD+Rs for my internal DVD+R, and I've been able to burn under XP with no problems.

---

### Post by reckless2k2 on 2007-08-01
install k3b and see if you get the same problems.

---

### Post by jon.reeve on 2007-08-01
OK, this is embarrassing. I figured it out right as I was posting the above. As it turns out, this DVD burner somehow doesn't like me to burn DVDs larger than 4 gigs or so. I was trying to burn 4.6 gigs, since the disc's label indicates that it can handle 4.7. I just deleted some files and tried again. This is probably going to become an issue though if I try to burn movies that are right at the 4.6 or 4.7 level.

---

### Post by neogus on 2007-08-30
yeah same problem here. When i try to copy dvds and i require near the 4.7GB the program dont recognizes the empty disc, i think its because is waiting for a 8.7 GB Disc.

---

### Post by tszanon on 2007-08-30
If I recall correctly, dvds can only handle 4.3 GiB. They say 4.7 GB because it handles about 4,700,000,000 bytes: 4,700,000,000 / 1024 / 1024 / 1024 = 4.3 GiB.

---

### Post by tphigginbotham on 2007-09-15
I'm having the same problem when burning CD's but it isn't a disk space issue. After adding the files to burn to the writable folder, I click the "Write to Disc" button, fill out the options, and receive the following error:

Insert a rewritable or blank disc
Please put a disc, with at least xxx MiB free, into the drive.  The following disc types are supported:
CD-R, CD-RW

I've tried multiple CD's and file sizes but always receive the same error. Before upgrading to Feisty, this wasn't an issue.

---

### Post by tphigginbotham on 2007-09-15
I just burned a CD with K3b without any problems. Ubuntu's default CD burning software appears to have the problem.

---

### Post by FuturePilot on 2007-09-15
> **tphigginbotham said:**
> I'm having the same problem when burning CD's but it isn't a disk space issue. After adding the files to burn to the writable folder, I click the "Write to Disc" button, fill out the options, and receive the following error:

Insert a rewritable or blank disc
Please put a disc, with at least xxx MiB free, into the drive.  The following disc types are supported:
CD-R, CD-RW

I've tried multiple CD's and file sizes but always receive the same error. Before upgrading to Feisty, this wasn't an issue.

Yes, I'm getting that too. The blank CD shows up on my desktop, so it is recognized, but then when I try to burn some files to it I get that error
```
Please put a disc, with at least xxx MiB free, into the drive.  The following disc types are supported:
CD-R, CD-RW
```
:confused:

---

### Post by princeza on 2007-10-26
I've now the same problem after upgrading to Gutsy Gibbons. On Feisty everything worked just fine. Any ideas? I've also tried burning with k3b.

---

### Post by junjan on 2007-11-03
Try Nero for Linux.

---

