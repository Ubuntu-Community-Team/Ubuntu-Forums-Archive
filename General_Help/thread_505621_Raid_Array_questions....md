---
title: "Raid Array questions..."
date: 2007-07-20
forum: General Help
---

### Post by mikey5555 on 2007-07-20
Hello All...

My wish is to utilize a Sun A1000 "Raid Array Box" as large drive to hold backup files when doing drive maintenance on various PCs, just in case it is needed.  I do this now with an external 25GB DAT tape drive - extremely slow, requires installing SCSI card and software to get the backup in many cases.  Occasionally the backup data is small enough to send to my local hard disk, but that is becoming less frequently the case.  So, I have a couple of SUN A1000 drive arrays with 12 SCSI drives in each one.  My UBUNTU is 7.04(?)  Feisty Fawn on an AMD processor pc.  I have installed the SCSI card, and can see 11 of the 12 drives when I go to the "Hardware Information" (Device Manager) item in the System>Preferences menu.  I would like to use these drives in a RAID5 configuration.  I have read several posts about using **mdadm** to do this.  There are so many different ways (according to the posts I've read) to configure RAID, that I have become confused.  
Here is the info about the drives as shown by Device Manager:
    [B] /dev/sdd
     /dev/sde
     /dev/sdf
     /dev/sdg
     /dev/sdh
     /dev/sdi
     /dev/sdj
     /dev/sdk
     /dev/sdl
     /dev/sdm
     /dev/sdn[/B]
All of these drives have existing partitions from a previous SUN System installation (they were gifted to me!),  What I would like is to get some instructions specific to preparing these drives for use in a new RAID Array consisting of 10 drives and either 1 or 2 spares (if I can get the system to find the 12th drive it'll be 2 spares).  I think RAID5 is going to be my preference due to the recovery capabilities when  drive problems crop up.  
Some pointers to get me started with implementing this as a RAID5 configuration will be most helpful.  I suspect I may have to delete the existing partitions on each drive (or maybe just format them) in order to use them the way I want: i.e. one LARGE drive.  As it will be used mostly for full backups of systems in for repair, this seemed to be most practical.  
Any suggestions, information, pointers, or articles (not to "general in nature" as I am easily confused by to much info and to many choices) would be very helpful.

Thanks....

Mikey5555

---

### Post by brent113 on 2007-07-21
I understand what you are saying.  I recently set up a raid 5 server, and it ended up taking me a while just to figure it out.

Here is what I followed, and it worked very well: [http://bfish.xaedalus.net/?p=188]("http://bfish.xaedalus.net/?p=188")

I was having some troubles with that but I ran e2fsck to fix errors and it fixed all the problems I was having.

Let me know if you have any other questions.

PS.  mdadm is smoking fast.  I only have a 3 drive array, and I benchmarked it at 50MB/s write, 100MB/s read, even on nearly 10 year old hardware.

---

### Post by mikey5555 on 2007-07-21
brent113,
    This article appears to be exactly what I need!  I will be trying this tomorrow (Sunday).  I'll let ya know how it goes....

regards...

mikey5555

---

### Post by fjgaude on 2007-07-21
> **brent113 said:**
> 

PS.  mdadm is smoking fast.  I only have a 3 drive array, and I benchmarked it at 50MB/s write, 100MB/s read, even on nearly 10 year old hardware.

Say, what program did you use to benchmark the array. I used dhparm -tT and got 114MB/s with three late-model Seagate SATAs in raid5. Am very happy with the speed. CPU is AMD 64 X2 4400+.

frank

---

### Post by brent113 on 2007-07-22
I used a program called bonnie++.  It's a fairly synthetic test, but it includes large contiguous reads and writes, random access, and a few other tests.  I've got a pIII 1GHz with 512MB pc133 ram, and it's got around 500 random accesses per sec and the specs above.  I'm using ubuntu server though, so it takes very little overhead to run (yay linux!)

I have 3 500Gig Seagate 7200.9s

---

### Post by fjgaude on 2007-07-22
> **brent113 said:**
> I used a program called bonnie++.  It's a fairly synthetic test, but it includes large contiguous reads and writes, random access, and a few other tests.  I've got a pIII 1GHz with 512MB pc133 ram, and it's got around 500 random accesses per sec and the specs above.  I'm using ubuntu server though, so it takes very little overhead to run (yay linux!)

I have 3 500Gig Seagate 7200.9s

Thanks, I'm installing it as I type. Will be interesting to see what results.

frank

---

### Post by iissmart on 2008-04-01
Sorry to bump an old thread, but I have just come across a Sun A1000 and would like to use it as well. Could you tell me what SCSI card you used to connect it to your system?
 
One thing I noticed is that this guide is how to configure it using software RAID, but the A1000 comes built in with a hardware RAID card. Is it possible to configure the hardware RAID in ubuntu (or any linux disto) or is software RAID the only way to go?

---

### Post by fjgaude on 2008-04-01
Hardware SCSI Raid cards, hmmm... you have to have a driver disk that Ubuntu will recognize to have it the kernel recognize such cards. Now, Linux knows SCSI but not the raid part of a SCSI built array.

Check to see if you can find such a Linux driver.

I don't use a SCSI card but use the SATA controller on my Gigabyte motherboard. It runs off the PCI-e bus at X1, which has a throughput of 500MB/sec, fast!

---

