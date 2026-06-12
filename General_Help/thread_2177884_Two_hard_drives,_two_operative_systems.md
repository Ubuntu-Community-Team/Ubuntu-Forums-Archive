---
title: "Two hard drives, two operative systems?"
date: 2013-09-30
forum: General Help
---

### Post by chrtylee on 2013-09-30
this seems like the proper place for this thread since im not really asking for support about my issue, just praising ubuntu. i was about to throw away 2 of my hdds when windows repeatedly failed to install on them...so i figured they were shot for whatever reason. then i said wtf ill try ubuntu and BAM! installed on both hdd with no issues. i just wish i could get my desktop to see 2 hdds properly so i can have windows on one for my school work and ubuntu on the other. why doesnt grub recognize os's from 2 hdds? or the BIOS for that matter... im confused about this.

---

### Post by Francisco Cardoso on 2013-09-30
You should see both of them. Have you checked if you have any raid set on BIOS?

---

### Post by chrtylee on 2013-09-30
no, not even sure if an option for it is there. i guess that could be the problem. i have dell bios i think a11 not positive though. also not sure if it matters that the hdds themselves arent connected i had to jack the cables from my disk drive to hook up the second hdd.

---

### Post by Francisco Cardoso on 2013-09-30
Can you check if you have one as primary and another as secondary?

---

### Post by chrtylee on 2013-09-30
if u explain? all i know is they are both sata drives, one is connected in the same place it was when i got the desktop, and the other is connected where the optical disk drive was connected. and i know nothing about making one master drive and one slave drive, if thats still a "thing"

---

### Post by poettone on 2013-09-30
You are correct, that is not required using SATA drives as they are "one drive" per cable connection, unlike PATA which allowed two drives on one ata cable. So this is not your issue. One thing I would check is that your BIOS shows both drives. If you do not see both drives in the BIOS then you do in fact have a failed drive or faulty cable or something like that. 

If you do see your drive in the BIOS and boot up Ubuntu then you can check to see if you can see the disk in /proc/partitions. by issuing the command  root# cat /proc/partitions  You should see 2 drives listed in there as sda, sdb etc.

let me know how things go.. Good Luck.

---

### Post by Francisco Cardoso on 2013-10-01
You havent refered the drive you had. In the BIOS or on the computer boot you must see both detected. If they are not detected. Then you must have a menu for SATA.

---

### Post by mörgæs on 2013-10-01
> **chrtylee said:**
> this seems like the proper place for this thread since im not really asking for support about my issue, just praising ubuntu.

The thread is turning into support, so moving to General Help.

---

### Post by chrtylee on 2013-10-01
well seeing as i installed ubuntu on it, i know the drive hasnt failed, i just cant get windows running on it. and the cable that has many colors does have a second connection on it, should i be using that instead of 2 separate cables? the 2 connectors are listed as p3 and p5

---

### Post by oldfred on 2013-10-01
Are these PATA drives not SATA drives?
       with pictures:
[http://en.wikipedia.org/wiki/Parallel_ATA](http://en.wikipedia.org/wiki/Parallel_ATA)
[http://en.wikipedia.org/wiki/Serial_ATA](http://en.wikipedia.org/wiki/Serial_ATA)
[http://en.wikipedia.org/wiki/Parallel_ATA#IDE_and_ATA-1](http://en.wikipedia.org/wiki/Parallel_ATA#IDE_and_ATA-1)

If PATA, are you using newer 80 conductor cable or the old 40 conductor cable?
      
 If you have the more modern 80 conductor 'cable-select' type of IDE ribbon cables, make sure the blue plug is connected to the motherboard, the grey plug is plugged into your slave drive (if any), and the black plug is plugged into your master hard drive.

   If you have the old kind of IDE ribbon cables, check that one hard disk is set as 'master' and the other is set as 'slave' if there's another drive on the same cable.

---

### Post by gretenov on 2013-10-02
Why would you install Ubuntu on two hard drives? Installing in just one is enough. The other can be used as purely storage.

---

### Post by mörgæs on 2013-10-02
Please read the thread thoroughly before posting.
In the original post it was stated that one disk should be used for Windows.

---

### Post by chrtylee on 2013-10-02
they are definitely sata drives. its the power cable that has the 2 connectors. and when i looked at that wiki page my power cables are identical to the ones on the SATA page.

---

