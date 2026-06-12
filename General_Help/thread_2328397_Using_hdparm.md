---
title: "Using hdparm"
date: 2016-06-20
forum: General Help
---

### Post by aaron50 on 2016-06-20
All,

I am very new to Linux, but i am setting up a server to be used as a file share and media streaming server, using Ubuntu 14.04. I have an external drive enclosure with 4x4TB drives. One will be used for all media, one for all private information and other files, then the other two are exact copies using rsync and rdiff-backup of the main drives. What I am looking to do is use hdparm to spin down the drives that are not in use and spin back up when i need them. Obviously the backup drives will only be needed when i am running a backup (hopefully via chron job), or restoring a backup. The other two would only be needed when called on for files or movies, pics, etc. I am not worried too much about a slight lag in the start up of the drive for accessing a movie, picture, or file. I am really looking to preserve the drives and reduce energy consumption. I have looked over the [manpage]("http://manpages.ubuntu.com/manpages/precise/man8/hdparm.8.html") of hdparm and everything is just going way over my head. I have also read a few [guides]("http://www.htpcguides.com/spin-down-and-manage-hard-drive-power-on-raspberry-pi/"), but i am not sure they do everything i need, or will be tailored to my needs. Any help you can give is greatly appretiated. The drives are /dev/sdb, /dev/sdc, /dev/sdd, /dev/sde. All have only one partition so sdb1, sdc1, etc. I am looking for a possible step by step recommendation of what you would use if you were building this sort of server, if you would be so kind. Please let me know if i need to provide more information. The drives are brand new Hitachi 4TB drives in a non-raid enclosure connected via usb, but eventually via esata.

---

### Post by TheFu on 2016-06-21
The 2nd guide looks fine. Are you using a Raspberry Pi?  Also, there are different models of Hitachi 4TB disks. The version matters since the 7200rpm and 5400rpm likely have different cmds.  Don't forget to enable SMART data on all the disks too.

---

### Post by aaron50 on 2016-06-21
No, I'm not using a raspberry pi. It is a traditional desktop build computer. Also, my disks are 7200rpm.

---

### Post by aaron50 on 2016-06-21
I have tried the process i mentioned above and i cannot seem to get my drive to spin down. I have it set to spin down at 15*5=75 seconds. After 10 min i typed sudo hdparm -C /dev/sdd and it says standby, i cannot seem to make the drive go to sleep, unless my command to see the status is waking the drive up.

---

### Post by TheFu on 2016-06-21
The command set for eSATA is different from that available to USB. eSATA is the same as SATA. Don't know if that matters for this stuff.  I do not allow any of my HDDs to spin down, ever.  Two camps of though around this ... that number of power cycles reduces total life of a HDD. That's what I believe.

Power use?  Guess that depends on your sensitivity.  I don't see much power use due to spinning disks.  According to the power company, my household is in the most efficient 2% of similar homes (whatever that means).

---

### Post by aaron50 on 2016-06-21
Okay, i will take what you do, and not spin down my drives. Thanks.

---

### Post by TheFu on 2016-06-21
> **aaron50 said:**
> Okay, i will take what you do, and not spin down my drives. Thanks.

Just to be clear, I don't know that there is proof for either choice, but if you have 7200rpm Hitachi disks, then I suspect they are designed to run 24/7/365.  It is the 5400rpm, slower, disks that usually spin down automatically.  There are many other very smart people who do spin down their HDDs, just like you were attempting.

Using eSATA would open up the full ATA command set too. USB3 bus has large throughput gains, well beyond what any storage besides RAM can keep up with, but the USB command set is slightly limited.

Unrelated to spinning down, but using **hdparm** to tune disk access can make a performance difference too.
[http://www.linux-magazine.com/Online/Features/Tune-Your-Hard-Disk-with-hdparm](http://www.linux-magazine.com/Online/Features/Tune-Your-Hard-Disk-with-hdparm)
and [http://blog.jdpfu.com/2011/10/17/hdd-performance-tuning-and-results](http://blog.jdpfu.com/2011/10/17/hdd-performance-tuning-and-results)
I was able to get a useful improvement by tuning each disk independently.

---

### Post by aaron50 on 2016-06-21
Thanks, I will look into those. Once i get my new motherboard i will be able to use eSATA, but at this moment i only have usb 2.0, very old motherboard. Im still looking at motherboards for my new server at this time, but if it doesn't have built in eSATA, i plan on putting a card in.

---

