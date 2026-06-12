---
title: "Ubuntu very slow when using hard disk"
date: 2007-05-19
forum: General Help
---

### Post by larini on 2007-05-19
Hi, I'm using ubuntu feisty and I note that it is very slow when has intense hard disk activity.

My system is an amd64 x2 4600, sataHD, 1GB  memory.

If I start coping a 5GB file from one folder to another, my system almost stop reponding until finish the copy.

What could be wrong?
Thanks.

---

### Post by jtraub on 2007-05-19
Probably your HDD  uses PIO method ([http://en.wikipedia.org/wiki/Programmed_input/output](http://en.wikipedia.org/wiki/Programmed_input/output)) instead of DMA. That causes high load of CPU.

---

### Post by larini on 2007-05-19
PIO? no, it is a SATA III hard disk (250 GB seagate)

Is ubuntu setting it to PIO some how?

---

### Post by bettlebrox on 2007-05-19
Sounds like you need to enable DMA on the drive. Install hdparm and look at this:

[http://demudi.agnula.info/wiki/DocumentsFaq#Harddrivespeedistooslow](http://demudi.agnula.info/wiki/DocumentsFaq#Harddrivespeedistooslow)

---

### Post by larini on 2007-05-19
hdparm is a tool only for IDE disks, isn't?

---

### Post by DBO on 2007-05-26
Getting the exact same issue... don't know what is causing it.  Interestingly hdparm reports that speeds are fine, but real to life testing (such as actually copying files) reveals I am getting under 10MB/s

---

### Post by larini on 2007-05-26
I just make the folowing test:

I install a fresh ubuntu feisty x86 and start copying a 4GB file from one place to another.
While copying, I start openOffice text app. It takes 1 minute and 5 seconds to open.

I Install a fresh fedora 7 over ubuntu and make the same test.
It takes only 37 seconds to open.

(and people is saying that fedora 7 is not compiled for performance yet..)

What is wrong with Ubuntu after all??

---

### Post by DBO on 2007-05-26
I notice you have SATA drives as well...  You dont happen to be using an nforce motherboard do you?  I have this feeling that the sata_nv module is to blame...

---

### Post by larini on 2007-05-26
Yes, I have an asus a8n with nvidia sata..

---

### Post by robert114 on 2007-05-30
Same problem with nforce 4 here too

---

### Post by matthias_k on 2007-06-24
Hi,

I have to say, I am experiencing heavy issues with hard disk I/O in Feisty as well (wasn't the case with Dapper and Edgy). For one, every once in a while the system completely locks up and outputs ATA disk I/O errors on the system console. The system always recovers after 30 or so seconds, but it's very annoying.

Second, I am noticing major slow downs when accessing the hard drive since the update. Working with a MySQL database has become ~4 times slower than before, which is unacceptable since we're executing very time consuming operations on a database.

Any ideas?

---

### Post by larini on 2007-06-24
I buy a new mother board and processor. Now I have a intel board 965 and E6600 processor.
Now I´m happy.

My old test gets now only 15 seconds!!
With amd and nvidia the time was 1 minute..

I love this intel solution.

---

