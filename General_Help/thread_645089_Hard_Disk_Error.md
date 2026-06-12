---
title: "Hard Disk Error"
date: 2007-12-19
forum: General Help
---

### Post by gary1163 on 2007-12-19
Hello all! lately I've been getting a ton of Sending Error Report messages , and also while booting up the system I sometimes get a Message that reads:

Primary Master Hard Disk S.M.A.R.T status Bad

Does this mean that my Hard Drive is on the Blink, or is there something else I can do? I've already ran a chkdsk, and I have other scheduled maintainence task. The only other major adjustments I've made was to set quota limits for the amount of disk space all Users can exceed, and to find some additional Disk Space, I lowered the amount space that is reserved for System Restore.Can some one help me with this problem?

:-k

---

### Post by Existentialist on 2007-12-19
SMART is the self-monitoring system of the hd, if it is saying there is a problem more than likley the hd is bad or will be going bad soon.  I use a program in windows called HDTune:
[http://www.hdtune.com/](http://www.hdtune.com/)
This will check differnt values SMART checks so you can see what exactly is giving the error.  Im sure hdparm or something in linux can do it also, but HDTune has worked well for me.

---

### Post by gary1163 on 2007-12-21
Existentialist,
Thanks for the link and the info, The results were: No Damaged Blocks, but the Health indicates everything OK, except for the Spin Up Time failed. Also I recently disconnected my hdd and found that one of the pins were bent under the master cable, I straightened it out and reconnected,think this will help? Because before I couldn't even Boot Up,
I was getting : DISK BOOT FAILURE,INSERT SYSTEM DISK AND PRESS ENTER :guitar:

---

### Post by Existentialist on 2007-12-21
> **gary1163 said:**
> I was getting : DISK BOOT FAILURE,INSERT SYSTEM DISK AND PRESS ENTER :guitar:

This seems to indicate it didnt even see the hd which would most likely be due to the pin.

---

### Post by gary1163 on 2007-12-21
Well it has been working ok since I straightend that pin, up until about an two hours ago, when I was just booted out, tried to restart and got the DISK BOOT FAILURE Message again, I did a hard boot and windows kicked in, Other people were suggesting that the boot order is out of wack in BIOS? Should my hdd be first then the CDrom? Also there was a suggestion of maybe a bad Master Data Cable? One other thing: Does it matter if the P4  cable or the P5 cable is connected to the hdd ( are these in relation to ATA or SATA ? Please advise and thanks for your continued help.


Gary
:guitar:

---

### Post by Sef on 2007-12-21
**Back up** all your data first.  If it is failing, you don't want to lose it all.

---

### Post by Sef on 2007-12-21
Dup post.

---

### Post by pyronaut on 2007-12-21
DEFINITELY AGREE WITH sef... BACK UP  disk before doing anything else... i have burned myself twice by not doing it and man was it a depressing trip :)

---

### Post by gary1163 on 2007-12-22
Ok! Backed up data! Now should I change the pecking order to hdd first then Cdrom, secondly if this does not work should I consider replacing the Master Data Cable, Thirdly does it matter if the P4 or P5 ATA  cable is connected to the hdd. Is there anything else I should consider or be doing?

Thanks Guys
Gary
:guitar:

---

### Post by Existentialist on 2007-12-22
I would put the primary hd as the primary boot device in BIOS.  And for the cable, you could try replacing it in case it went bad.  As for ATA-4 or 5, it shouldn't matter, I believe that the only difference is the ATA-5 is an 80 wire cable rather than 40 so that each wire has its own ground rather than sharing a common ground which increases transfer rates.  For your case of testing if it fixes the problem of booting either cable should suffice.

---

### Post by gary1163 on 2007-12-23
Ok here's what I got: I left the ATA-5 cable connected, switched the Master data Cable, and I think in BIOS I have my Primary HDD first, But when I run a msconfig and I look under BOOT.INI and click on check all Boot Paths I get the following message: It appears that the following line in Boot INI File does not refer to a valid Operating System:C:\CMDCONS\BOOTSECT.DAT=MICROSOFT WINDOWS RECOVERY CONSOLE/CMDCON would you like to remove the BOOT.INI. file. Also my default reads: MULTI(0)DISK(0)RDISK(0)PARTITIONS(2)\WINDOWS
Also when I ran HDTUNE hthe results were as follows: Transfer Rate:  
Minimum= 6.2 mb/sec
Maximum= 59.8 mb/sec
AVERAGE= 46.8 mb/sec
ACCESS TIME= 13.9m s
BURST RATE= 72.2 mb/sec
CPU USAGE= 18.4%

Don't know if any of this helps diagnose my problems..Just in case could you walk me through the BIOS procedure of making sure my HDD is first..

Thanks
Guys
:guitar:

---

