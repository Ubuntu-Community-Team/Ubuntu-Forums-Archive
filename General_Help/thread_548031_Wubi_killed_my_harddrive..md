---
title: "Wubi killed my harddrive."
date: 2007-09-10
forum: General Help
---

### Post by Lokito on 2007-09-10
Yes, it did.  Someone other than me clicked something during installation, and something went wrong.  Whenever I boot, I'm unable to boot in either WIN XP or Ubuntu.  Various ways of booting give me various error codes.  I've brought in my computer for repair, but they told me they'd have to wipe it and reinstall, which is something I *really* don't want to do.  First error:

Physical disks:
Port Drive Model          Type/Status (Vol ID)
0    Maxtor 6Y160M0    Member Disk (0)
2    Maxtor 6Y160M0    Error Occurred (0)

I get a message that "Drive 1 not found:" and "Drive 3 not found:"

Hitting F1 brings me to the OS booting choice page.  If I hit WIN XP Professional, the splash screen shows up but displays indefinitely.  No matter how I try to boot, it's unsuccessful.  I've tried a Knoppix CD, but my system doesn't detect it automatically on booting, and when I go to the Boot Device Menu and select the "Onboard or USB CD-ROM Drive" option, I get a "selected boot device not available" error.

On to unbuntu.  When I choose Ubuntu at the OS Choice screen, it starts to load, and a bunch of MBR errors go flying by.  "MBR cylinders not equal to the BIOS one", "MBR total sectors greater than the BIOS one", etc.  Then I get this:
ERROR: dos: partition address past end of RAID device.
ERROR: dos: partition address past end of RAID device. 

Then, after a minute or so, this appears:

/bin/sh: can't access tty; job control turned off

I assume everything shows up twice or more because I have a dual harddrive.  It's clear that the major problem is a RAID error, but I've tried everything I know (albeit, not that much) to try and fix it, and the guys who tried to repair it didn't even try the simplest things, like using a LiveCD.   I don't care about my system, but I *need* to retrieve some of my files before I wipe it and start over.  You're the Wubi guys - what went wrong, and can this be fixed?

---

### Post by ago on 2007-09-11
> **Lokito said:**
> Yes, it did.  Someone other than me clicked something during installation, and something went wrong.

Do you use a RAID 0? Software RAID maybe? It's possible that Wubi did not understand that and tried to install on 1 of the 2 HD and hence the 2 HD are no longer in sync. That should be recoverable though, but the solution depends on the Raid you are using.

Other common cause of problems are hard-reboots. This is normally fixed by running chkdsk /r.

For Ubuntu look at the size of disks in c:\wubi\disks. If any of them is 0 size, that's the issue (that's a bug with 64bit machines, selecting installation size > 4GB).

---

### Post by Lokito on 2007-09-11
It should be noted that I don't know much about operating systems, especially anything linux.  

One is definitely raid 0.  I'd assume they'd both be, but I'm not sure.  If the other isn't RAID 0, is that a problem?  

I can't run chkdsk.  System came preinstalled with XP, no disk.  I tried Knoppix, and I tried Ultimate Boot CD.  The system isn't recognizing disks.  Is there any alternative?

How do I check c:\wubi\disks ?  I have a very limited scope of anything on the system.

When I installed wubi, it was my first alternate OS install.  Also, a family member hit something during installation that may have caused the problem.  After it installed, XP was still working.  However, the next time I booted the computer, I got the errors listed above.

---

### Post by ago on 2007-09-11
> **Lokito said:**
> One is definitely raid 0.  I'd assume they'd both be, but I'm not sure.  If the other isn't RAID 0, is that a problem?
A raid 0 spans over 2 disks with each pieace of data being on only one of the 2 disks, in raid 1 your data is duplicated on each disk. In either case if one HD is in raid, the other is too. RAID 0 is by far the most unsercure combination, more unreliable than a single hard disk (let alone than raid 1) and would be the most difficult to recover if anything goes wrong, it's normally a bad idea to put any non-temporary data in there. 

> I can't run chkdsk.  System came preinstalled with XP, no disk.  I tried Knoppix, and I tried Ultimate Boot CD.  The system isn't recognizing disks.  Is there any alternative?
You need to boot the machine from another medium, if CD is not an option, you can use USB memory key (if USB booting is supported) or ethernet booting (requires a second machine on the network properly configured) or a floppy.

> How do I check c:\wubi\disks ?  I have a very limited scope of anything on the system.
You do that after you recover of course

> After it installed, XP was still working.  However, the next time I booted the computer, I got the errors listed above.
Hmm it is unlikely to have much to do with wubi in this case.

---

### Post by Lokito on 2007-09-11
> **ago said:**
> A raid 0 spans over 2 disks with each pieace of data being on only one of the 2 disks, in raid 1 your data is duplicated on each disk. In either case if one HD is in raid, the other is too. RAID 0 is by far the most unsercure combination, more unreliable than a single hard disk (let alone than raid 1) and would be the most difficult to recover if anything goes wrong, it's normally a bad idea to put any non-temporary data in there. 


You need to boot the machine from another medium, if CD is not an option, you can use USB memory key (if USB booting is supported) or ethernet booting (requires a second machine on the network properly configured) or a floppy.


You do that after you recover of course


Hmm it is unlikely to have much to do with wubi in this case.

I had a flash drive I could try.  But I doubt it will work.  Once I'm at the Boot Device Menu, I hit "Onboard USB or CD-ROM Drive" and the CD doesn't work.  Since it's the same option for a flash disk, that won't work either, right?  Also, what would I put on it for booting?

Well, I should re-word my description of XP.  It was working, but some features were acting funny.  This happened immediately after the Wubi install, and I had nothing else going on that could have affected the system in that way, so the problem has to be something to do with Wubi.

---

### Post by EnergyRecrui on 2008-11-18
The reasons that people want to be able to use Linux instead of Windows are obvious; Ubuntu is free both in terms of beer and speech, which means that you can save money by not having to pay out for expensive software, benefit from the support of an active community which is behind the code and buy into an idealistic, anti-monopolistic movement which hopes to change the world.
Until fairly recently, however, Linux on the desktop has been the preserve of the people who programmed it in the first place; the mantra of ‘by geeks for geeks’ has often been used to describe it. However, this is now changing.

---

### Post by Yownanymous on 2008-11-19
> **EnergyRecrui said:**
> buy into an idealistic, anti-monopolistic movement which hopes to change the world.

I think buying into the movement rather defeats the point.:lolflag:

---

### Post by john methew on 2008-11-29
You can get more details from here about raid 0. [http://en.wikipedia.org/wiki/Redundant_array_of_independent_disks](http://en.wikipedia.org/wiki/Redundant_array_of_independent_disks)
Its easy to use and handy tool.

---

### Post by dball1968 on 2008-11-30
I had a lot of trouble with RAID on my hard drive and installing some programs.

I eventually dumped the RAID and life was much easier after that.

Also, next time you install, get a big slobbering guard dog to keep people away from your keedboard and mouse.

:O)

---

### Post by Dareajoe on 2009-01-27
How to connect a Maxtor external hard drive to a laptop?I'd like to know how to connect a Maxtor external hard drive to a laptop. What kind of connector should I use? Thank you.

---

