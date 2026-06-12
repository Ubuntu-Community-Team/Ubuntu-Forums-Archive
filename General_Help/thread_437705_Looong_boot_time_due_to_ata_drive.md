---
title: "Looong boot time due to ata drive?"
date: 2007-05-09
forum: General Help
---

### Post by Arbi on 2007-05-09
I'm a new linux user, installed it a couple of months ago and had relatively no problems that I couldn't solve by googling it. But after upgrading to feisty, I noticed I had a really slow and long boot time. And even before feisty, edgy sometimes wouldn't boot (gets stuck at Loading, no boot screen). Feisty has this to say in /var/log/dmesg

```
[   57.407688] ata2.01: qc timeout (cmd 0xa0)
[   57.407723] ata2.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[   57.407787] ata2.01: (BMDMA stat 0x65)
[   57.407843] ata2.01: cmd a0/01:00:00:00:00/00:00:00:00:00/b0 tag 0 cdb 0x12 data 254 in
[   57.407846]          res 51/51:03:00:12:00/00:00:00:00:00/b0 Emask 0x5 (timeout)
[   64.407212] ata2: port is slow to respond, please be patient (Status 0xd8)
[   87.395377] ata2: port failed to respond (30 secs, Status 0xd8)
[   87.395448] ata2: soft resetting port
[   87.723071] ata2.01: failed to IDENTIFY (I/O error, err_mask=0x1)
[   87.723081] ata2.01: revalidation failed (errno=-5)
[   87.723164] ata2: failed to recover some devices, retrying in 5 secs
[   92.724976] ata2: soft resetting port
[   93.064930] ata2.00: ata_hpa_resize 1: sectors = 160086528, hpa_sectors = 160086528
[   93.076913] ata2.00: ata_hpa_resize 1: sectors = 160086528, hpa_sectors = 160086528
[   93.076918] ata2.00: configured for UDMA/33
[   93.248549] ata2.01: configured for MWDMA2
[   93.248612] ata2: EH complete
[   93.249682] SCSI device sda: 160086528 512-byte hdwr sectors (81964 MB)
[   93.252481] sda: Write Protect is off
[   93.252492] sda: Mode Sense: 00 3a 00 00
[   93.266403] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   93.269112] SCSI device sda: 160086528 512-byte hdwr sectors (81964 MB)
[   93.270466] sda: Write Protect is off
[   93.270471] sda: Mode Sense: 00 3a 00 00

```
After this it just repeats itself for about 4 more times before it boots to the login screen, thus, it takes up to more than 5 minutes just to boot up my computer, where the log ends at "[  312.738831] eth0: no IPv6 routers present" I presume.
What's going on? How can I fix this?

---

### Post by Arbi on 2007-05-10
I hope I don't have to wait so long to boot up linux, can anyone help me?

---

### Post by GreenMamba on 2007-05-18
I'm having the same problem in Xubuntu 7.04 ... any help from the experts?

---

### Post by LukeCarrier on 2007-05-20
I'm having exactly the same problem, I suspect it is down to my CD-ROM drives. I have checked all the hardware over, and all the drives are set up as follows:

Primary Master:       Hard Disk
Primary Slave:         None
Secondary Master: DVD-RW Drive
Secondary Slave:    CD-RW Drive

Is it to do with this? Please can we have some help here? :confused:

---

### Post by RedSquirrel on 2007-05-20
Try doing some searches on launchpad. Here's one thread that might help:

[https://bugs.launchpad.net/ubuntu/+bug/104581](https://bugs.launchpad.net/ubuntu/+bug/104581)

---

### Post by Ub1476 on 2007-05-20
Boot in safe mode, so can you see what it uses so long time to fiure out at:)

I didn't have the same problem, but by editing the network interfaces in /etc/network/interfaces, Ubuntu will boot faster anyway. I removed everything except for the loopback one.
NOTE: if you remove them, write them down before you do! Then you can edit the interfaces file if system crashes.

---

### Post by RedSquirrel on 2007-05-20
I believe the error is this:

> exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen

One solution presented in the link I gave above suggested that you put a CD in the drive and that will solve the problem. :lol:

---

### Post by alex77 on 2007-10-02
I have the same problem, except i am using gutsy beta.
 its also different ata port numbers it gets stuck on every time, seemingly in an endless loop. I left it going for an hour and it still did not boot.

I tried putting a cd in the drive ( i have one sata HDD, one IDE dvd drive) and this made no difference.

Funny thing was, the first time it booted up there was no problem (from clean install overwriting feisty, using alternate beta cd) , and i didnt change anything...

Is there a way to fix this problem during booting? like skipping the bit where it checks the sata ports?

 I know gutsy is just in beta, but it would be nice to make this problem go away. Hopefully the stable release will work. Fingers crossed...

---

### Post by alex77 on 2007-10-24
Got mine working. 

solution: > **alex77 said:**
> Solved, I had set my dvd drive as slave when it was the only thing on the cable. Guess this confused things. Anyhoo, set it to master and all works lovely now.

---

### Post by szandor on 2008-02-08
> **alex77 said:**
> Got mine working. 

solution:

old thread but newest one i could find. did your problem remain resolved? most of the topics that discuss this issue point to the cdrom/dvd drive being set as master/slave/what not. obviously, the first solution is to disconnect the drive. horrible. or pull out the drive and change the cable select. just wanted to follow up and see if setting the drive to master kept the issue resolved. i believe mine is set as slave, but i'll have to check.

---

### Post by alex77 on 2008-02-09
yep, it all still works fine. I also have irqpoll noapic and nolapic added to my kernel options.

---

### Post by szandor on 2008-02-10
cool. thanks for the info. perfect timing.  today's the day i shut down my server.

---

### Post by szandor on 2008-02-10
well, i set the dvd drive to master and added the kernel options and so far no ata errors in syslog for the last 12 hours. this is the longest it's gone without errors and hdparm isn't hanging. so far so good.

---

### Post by szandor on 2008-02-11
over 24 hours now. hell yeah, finally. thanks again alex77. i've seen other posts in regards to this issue but you're the first one i've seen that's followed up with status and what was done. another reason i love this forum even though i haven't seen ubuntu. you guys fix all my obscure fedora/linux issues. :D

---

### Post by crtlbreak on 2008-06-23
Using Hardy Alternate Install ubuntu-8.04-alternate-i386.iso
And wanting to upgrade to an 80GB from 20GB ATA disk.
I first attempted to rewrite my whole system with dd to the larger ATA disk - when rebooting with the new disk in place as master I was getting weird startup errors such as

revalidating (errno=-5) and 
ata1.01: exception Emask 0x0 

there were no issues with the previous 20GB disk - let sleeping dogs lie? :)

Then I attempted to re-install on the new disk from scratch 
I too was having extended boot/installation times and similar error messages <DRDY ERR> and  looooonnngggg delays between the text install options.
A lot more reading of forums and I disconnected the CD-R+- drive and only left the DVD-ROM connected as master - presto - all error messages gone and fast installation times etc  - all as expected.

I also read somewhere (i cannot remember which page of all those I trawled through) that the system is confused between Serial ATA and ATA - although it seems the CD-ROM conflict was the more evident issue in my system. It is now disconnected while I install and continue on my merry way.
Just thought I would share my own experiences with everyone so it endorses your findings.
Regards

---

