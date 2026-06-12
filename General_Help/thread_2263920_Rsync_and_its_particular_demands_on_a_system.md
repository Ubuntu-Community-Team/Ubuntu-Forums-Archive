---
title: "Rsync and its particular demands on a system"
date: 2015-02-04
forum: General Help
---

### Post by david_silvester on 2015-02-04
Hi guys,
New to the forum (just registered) have been using linux for a few years and have used ubuntu for a large proportion of that.
I still consider myself quite a beginner though.

I have a question about rsync:

I am using rsync over ssh as a method of backing up data from remote machines onto a single rsync backup server.

Currently I dont use ubuntu, but I am looking at a new server that I am planning to run ubuntu on, for this purpose.

I am concerned about how many concurrent tasks the server will accept from remote rsync backup clients.

I just wondered if anyone has some details about where the largest demands come from when receiving data via rsync, and what components are under the most strain?

thanks in advance.

---

### Post by SeijiSensei on 2015-02-04
Under the most strain?  The hard drive.  Everything else is just electronics.

I don't think multiple streams would pose as great a problem, though if you're backing up multiple servers, I'd stagger the jobs when setting up crontab.

---

### Post by david_silvester on 2015-02-04
> **SeijiSensei said:**
> Under the most strain?  The hard drive.  Everything else is just electronics.

I don't think multiple streams would pose as great a problem, though if you're backing up multiple servers, I'd stagger the jobs when setting up crontab.

Hi thanks for the quick reply.

I am planning to stagger the backups (actually I am using backup assist at the client side) - but even fully staggered through 5pm - 8am I am going to have at least 6 concurrent tasks at any one time.

OK, I am glad you said hard drive - on the new system I am looking at it has dedicated SAS controller and it has 12 drives - I am not sure of the configuration I will have yet, but would it be likely so run better seeing as backups would be going to different drives?

I also get the impression from what I have read that decompression and decryption also play a big part in the amount of resources used at the server side, is that right?
If so I am considering also lowering both of those things.

---

### Post by SeijiSensei on 2015-02-04
I'd try some tests with gzip enabled versus disabled (the "-z" option in rsync).  On high-speed connections compression may just add unnecessary overhead.  I've rarely found SSH encryption to add much overhead at all.

If you consider a RAID solution, I'll just mention that RAID generally degrades write performance since multiple copies of the data must be written across the array.  You might find a better solution is to dedicate a single drive to backing up each of the remotes.  Before you go too far down the road with this, I'd recommend reading up on the performance implications of various RAID solutions.

If you're just keeping an up-to-date image of the remote's drive, rather than completely re-imaging all the remote disks every day, you may find that rsync will transfer fairly small amounts of data each day.

---

### Post by david_silvester on 2015-02-04
> **SeijiSensei said:**
> I'd try some tests with gzip enabled versus disabled (the "-z" option in rsync).  On high-speed connections compression may just add unnecessary overhead.  I've rarely found SSH encryption to add much overhead at all.

If you consider a RAID solution, I'll just mention that RAID generally degrades write performance since multiple copies of the data must be written across the array.  You might find a better solution is to dedicate a single drive to backing up each of the remotes.  Before you go too far down the road with this, I'd recommend reading up on the performance implications of various RAID solutions.

If you're just keeping an up-to-date image of the remote's drive, rather than completely re-imaging all the remote disks every day, you may find that rsync will transfer fairly small amounts of data each day.

Hi, thanks for the info.
Good point about the RAID. I am yet to see exactly what options I have. perhaps if there is some other options than RAID1 I can get something that will offer good performance. But I will read up on that.

And yes, re the transfer of data - I looked at bandwidth graphs and its very small amount of data that we transfer - just a few GB per night across all of our backups (40+). So perhaps compression off would be a good idea.

---

### Post by david_silvester on 2015-02-05
Hi SeijiSensei,
Just wondering if you could provide a little more help regarding RAID levels - I am thinking about RAID 6 with 12 SAS drives. would that produce a reasonable performance?
At the moment I am writing to individual unraided drives, so just wondering what the performance difference would likely be?

Also, I am looking at software raid, is there a great performance loss in that over hardware raid?

---

### Post by SeijiSensei on 2015-02-05
I'm no expert on RAID solutions beyond a couple of simple RAID1 and RAID5 setups.  

Since you have a SAS controller, I'd use that instead of software RAID if it provides the options you want.  If not, then software RAID is fine. I doubt it would be much slower than the controller since you're using the machine's CPU, which is probably at least as fast as the one on the controller.  I manage one machine using an LSI/Symbios controller on which we have CentOS 6.5 installed with two drives in RAID1.  It was detected during installation and the required kernel modules were added automatically.  I believe I had a similarly positive experience testing Ubuntu on this machine, but I routinely use CentOS on servers and Ubuntu on desktops.

The only way to answer your questions is to run tests.

---

### Post by david_silvester on 2015-02-05
Thanks. Yes I use CentOS quite a lot as well. OK, I think I am going to go for RAID 6. Still doing testing at the moment on how many concurrent rsync tasks I can run on particular hardware if that goes well I'll get the new system up and running.

---

### Post by btindie on 2015-02-05
Take a look at these links regarding the SSH cipher, it can affect the speed quite a bit depending on how much you're transferring.

[https://bbs.archlinux.org/viewtopic.php?id=9107](https://bbs.archlinux.org/viewtopic.php?id=9107)
[http://blog.famzah.net/2010/06/11/openssh-ciphers-performance-benchmark/](http://blog.famzah.net/2010/06/11/openssh-ciphers-performance-benchmark/)

---

### Post by SeijiSensei on 2015-02-05
The first article is from 2005, and the second uses a system "similar to a Pentium @100 MHz."  Neither of these is especially pertinent when looking at contemporary CPU speeds.

---

### Post by david_silvester on 2015-02-05
just trying to decide between raid 5 or 6 now. How big a difference is there in performance between the two?

---

