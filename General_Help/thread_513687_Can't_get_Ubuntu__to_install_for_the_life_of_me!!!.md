---
title: "Can't get Ubuntu  to install for the life of me!!!"
date: 2007-07-30
forum: General Help
---

### Post by -RYknow on 2007-07-30
Hey all, First off I would just like to say, I'm new to Ubuntu, but not new to computers. My problem is I can not for the life of me get Ubuntu installed on my server. Here are the system specs:

CPU: AMD Athlon 64 3700+ (OC'ed to 2.71)
RAM: 2 gigs Corsair XMS DDR400
Mobo: Asus A8N SLI Premium
GPU's: Dual 7800GT's in SLI
HD's: 2x Western Digital 160 gigs, 2x Western Digital 500 gigs, and 1 Seagate 400 gig. 
PSU: PC P&C 510 SLI
Drive: 1 Lite on CD burner/DVD player combo drive.

Note: The drive I'm trying to get this installed on is a 160 gig WD drive, with a 50 gig partition for XP, and the rest is left for Ubuntu. 

Ok...so two days ago I installed Ubuntu on my older Socket A system and that installation went off without a hitch. It was a very pleasant experience. However...trying to get Ubuntu installed on this system has been a nightmare. At first, I left everything installed and tried to install Ubuntu...no luck...just get a read error of some kind (I'll post back the message I get). I then thought maybe it had something to do with the SLI, so I removed one of the 7800GT's...still not luck. At this point...I removed all HD's except the one I want Ubuntu on, still no joy!

At this point I went on to redownload Ubuntu (64 bit version), reburned, and went through the entire process again. Still no luck! I tried to install with the same disc I used on the Socket A machine, same thing. I'm not sure what else to try. I'm going to try pulling my CD-rom out of the machine with the Socket A system...and try that. If that doesn't work...what else can I try? I've tried everything I can think of. 

Thanks for any help in advance. 
-RYknow

---

### Post by FleetAdmiral74 on 2007-07-30
You can refer to [http://ubuntuforums.org/showthread.php?t=500020](http://ubuntuforums.org/showthread.php?t=500020)

And post that read error when possible, should help

---

### Post by fjgaude on 2007-07-30
I have the same motherboard and it has been a pain to get Ubuntu to install. But, it seems it worked okay with Feisty, 32-bit... I don't think I was ever able to install the 64-bit version of Edgy, and any of the betas going back a year or so didn't work either. I've never been able to get suspend or hibernate to work on this MB.

The first time I used the character-based version to get going and then added the nvidia driver. I have one gforce 3600 GS. It's fast.

Good luck,

frank

---

### Post by -RYknow on 2007-07-30
I wasn't able to get the 32bit version to work either. I've gone as far as trying serial keyboard and mouse...USB keyboard and mouse, I even pulled a CD rom out of another machine to try it...as well as a DVD rom...thinging maybe my combo drive was the blame for the read error. Still no luck. 

The error I get with the 32 bit version is:

I hit the install Ubuntu, and then it brings up the grey box that says "Loading Linux Kernal". It goes to 3% and freezes there. At this point a little error message pops up as, "I/O Error -- Error reading boot CD." At the top of the screen there is some white text that reads: "loading isolinux: Disc error32, AX= 4280, drive 9F"

A quick google search and people seem to suggest that this is caused be a currupt disc. I used this very same disc to install Ubuntu on the machine I am writting from now.

Any suggestions would be great! Thanks!
-RYknow

---

### Post by merlinus on 2007-07-30
Perhaps it is your cd drive.  This happened to me.

You can try cleaning the lens, or install the drive from another computer.

-merlin

---

### Post by fjgaude on 2007-07-30
You know I'm thinking back as to how I first got Ubuntu Edgy installed. I first installed Fedora 5, then partitioned the disk in half leaving Fedora on, and installed Ubuntu on the remaining uninitiated half. Then I deleted Fedora. Then, believe it or not, I installed Feisty on that unused partition without a problem from the live CD.

Wow, believe it or not... I later thought it must be the large 320G drive I am using, but still can't say for sure.

Anyway, it seems I'm okay, and have three other drives, each 300G, in a raid5 array mounted on /home. Both that array and the 320G work together smartly.

Can't offer any more help than this.

frank

---

