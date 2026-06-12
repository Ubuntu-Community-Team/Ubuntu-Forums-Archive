---
title: "Trouble Creating Working iso"
date: 2015-04-24
forum: General Help
---

### Post by ross4 on 2015-04-24
I have Lubuntu installed on a very, very old Toshiba Laptop Satellite 500 and Xubuntu installed on an old Toshiba Satellite P100. For fun and education, I want to try a few other light-weight Linuxes on the Satellite 500. However, I have run into a problem. Using xfburn on the newer P100, I downloaded and burned an iso for a Linux called Porteus on a CD but it would not boot on the Satellite 500. It did boot (IE booted to the live version) on the P100. To test the CD drive on the Satellite 500, I tried booting to my original Lubuntu CD on that machine and that worked also. I then tried downloading, burning etc. on the old, old Satellite 500, once again using xfburn. That would not boot on the 500 but did on the P100.


  Any suggestions as to what might be going wrong?
  
I was wondering if the problem might be with xfburn but I cannot remember what program I used to burn the Lubuntu CDs, which do work on both computers.

---

### Post by ian-weisser on 2015-04-24
Is the 500's BIOS set to boot from a CD? Does the CD drive work?

---

### Post by ross4 on 2015-04-24
As I point out in the original message, the CD drive does work. I can boot the Lubuntu CD from it.
When I try the other problem iso-CD, I set the machine to boot from the CD. 

One thing I did not mention. When I put the problem iso CD in the drive when Lubuntu is running, the machine sees it as a blank, unformatted CD with no files. In my other computer it comes up as it should with various files on it.

---

### Post by scdbackup on 2015-04-25
It seems that the drive in the problematic machine cannot read the individual CD, whereas it can read others. Burn the ISO to another CD medium and try again. Best use a CD of different brand or medium type (CD-R versus CD-RW). Use the youngest burner drive you have in reach. 
 
> I was wondering if the problem might be with xfburn 

Rather not. Firstly the CD boots on other machines, secondly Xfburn does not add any information to the ISO when it gets burned onto medium. All boot stuff is already present in the ISO.

---

### Post by ross4 on 2015-04-25
> **scdbackup said:**
> It seems that the drive in the problematic machine cannot read the individual CD, whereas it can read others. Burn the ISO to another CD medium and try again. Best use a CD of different brand or medium type (CD-R versus CD-RW). Use the youngest burner drive you have in reach. .

Ok, I'll give that a try. I was using a CD-R but I'll try a different manufacturer, maybe. Pretty sure that CD-RW CDs are not worth looking into.

I'll be away from my machines for a while but I think I'll eventually try to determine what I did to get the working iso's. I think I was working in XP when I did them. Might make a difference. Sometimes I believe that doing things on computers is like doing magic: You have to have the correct incantations and hand/wand waving down just so. Also, you must be aligned with the proper ley lines. Any minor change in these, and you are out of luck...

Ross

---

### Post by scdbackup on 2015-04-26
There is not much reason to suspect the quality of the ISO
as long as a booted Lubuntu and the CD drive report the CD
as empty.

Nevertheless i looked at [http://build.porteus.org/](http://build.porteus.org/) and see
a configuration option EFI, which would possibly sabotage
booting on an old BIOS based machine. Funny concept to 
get an ISO. I choose 64 bit EFI and wait for a 66 MB ISO ...
can it be it waits for a donation now ?
Let's try [http://dl.porteus.org/x86_64/current/Porteus-XFCE-v3.1-x86_64.iso](http://dl.porteus.org/x86_64/current/Porteus-XFCE-v3.1-x86_64.iso)
... it's oldfashionedly BIOS bootable from optical medium.
No boot sector for EFI, no isohybrid for USB stick.

  > Sometimes I believe that doing things on computers is like doing magic 

Yes and no. The miracle is that all software bugs are 
explainable but many of them still look like the work of
evil spirits.

Your problem is most probably just a failure of physics
between laser and CD dye. The drive firmware decides that the
medium is not readable. Several layers of operating system
software and desktop further interpret this until you get
to see the message on the screen. This adds fairies and goblins
to the mundane hardware failure.

One can peek at the drive's perception of the medium by
watching the SCSI command transactions of a burn program
when it inspects the drive.
E.g., while the problematic CD is inserted:
```
xorriso -scsi_log on -outdev /dev/sr0 -toc 2>&1 | tee -i /tmp/xorriso_log
```
The file /tmp/xorriso_log will catch the many output lines
among which one will probably find drive reactions like
```
+++ sense data = 70 00 02 00 00 00 00 0A 00 00 00 00 3A 01 00 00 00 00
+++ key=2  asc=3Ah  ascq=01h
```
which would mean that the tray is loaded but no readable
medium is detected.

---

### Post by ross4 on 2015-11-07
I believe I found the cause of the problem. A short while ago I bought a new package of CD-Rs and, after doing the little projects that I needed them for, I came back to the ones that precipitated this thread, used the new disks and I had no problem related to reading them. So I'm guessing that faulty media was the source... unless the Good Linux Fairy visited my machines one night and removed the hex put on them by the evil Windows Troll. Thanks for the various suggestions. 
Regards,
Ross

---

### Post by sammiev on 2015-11-07
I have two Toshiba Laptop Satellite 500's that can boot from DVD/USB working great with 14.04... and beyond. I beefed up the memory some years a go.

I never tried CD-Rs in years so I'm not much help there.

---

### Post by sudodus on 2015-11-07
> **ross4 said:**
> I believe I found the cause of the problem. A short while ago I bought a new package of CD-Rs and, after doing the little projects that I needed them for, I came back to the ones that precipitated this thread, used the new disks and [COLOR="#2F4F4F"]**I had no problem related to reading them. So I'm guessing that faulty media was the source**[/COLOR]... unless the Good Linux Fairy visited my machines one night and removed the hex put on them by the evil Windows Troll. Thanks for the various suggestions. 
Regards,
Ross

Congratulations and thanks for sharing the solution :KS

Please click on **Thread Tools** at the top of the page and mark this thread as SOLVED

---

