---
title: "mount windows drive in linux corrupt files"
date: 2008-06-02
forum: General Help
---

### Post by skoberlink on 2008-06-02
I recently installed ubuntu on a 120 GB IDE seagate.  I also set it up for a dualboot with a vist home premium install on a 400 GB IDE Seagate.  Windows is slave, ubuntu is master.  I keep music files etc on the 400 gb.  Chose that one cause i wasn't sure if windows would play nice with the linux drive ubt i knew linux could access the windows drive.  I set up the bootloader and whatnot and tested both OS's to make sure they work.  no problem.  I set up ubuntu and have been using that the last couple days.  I couldn't get my mic to work in ubuntu so I went to try it in windows.  I loaded it up and it was really slow.  When it finally did load up i logged in and immediately got an alert saying that (filepath)\Prefetch is corrupt run Chkdsk.  I was then flodded with more prefetch alerts as well as other programs.  I ran chkdsk and it turns out a ton of stuff is unreadable on the 400 GB.  So I put in the Vista Install Disk and ran repair and it couldn't find the vista install so i hit next anyway and told it to do a startup repair.  It said there were drives errors may take over an hour to repair blah blah blah.  I cam back about 15 min later and it said it couldn't fix the problem.  So here's my question:

Are the files corrupt because I mounted the drive in ubuntu or is the problem unrelated?

If it is because I mounted it, can it be fixed in Ubuntu or Windows?

If the corruption can't be fixed how can I save my program settings/files (no files or anything fresh install on a homebuilt PC but I spent a lot of time getting better versions of programs i.e. firefox + extensions and I don't want to do all that again).

in addition to the last question my first idea is to copy all the program files etc. over to the linux drive and reinstall windows and and the programs and then copy back in the program files to get my settings, thunderbird e-mail accounts, etc. back.  Will that work?

Sorry for the long post I would appreciate any help you guys can give me.

EDIT: Alright I just tried to mount the drive in ubuntu and it said it couldn't and that i need to "...run chkdsk /f in windows..." so I assume that this means the mounting isn't the cause it's just having some sort of problem.  Anyway tried to boot into vista again and told GRUB to boot vista and it went to  "Starting Up..." and hangs i left it for a couple minutes then came to my macbook to post this so I'll keep updating if anything interesting happens...

EDIT2: OK continues to hang at Starting up... so I shut it off and restarted from windows install disc and ran command prompt and put in chkdsk /f (enter).  It said "The typ of the file system is NTFS.  Cannot lock current drive.  Windows cannot run disk checking on this volume because it is write protected."  Evidently this is a windows problem and unrelated to my linux install so I'll stop posting unless replies appear.  I'd appreciate help if you've got it but this isn't a windows forum so i'll take my problems elsewhere.

---

### Post by rubicon on 2008-06-02
> **skoberlink said:**
> It said "The typ of the file system is NTFS.  Cannot lock current drive.  Windows cannot run disk checking on this volume because it is write protected."Never experienced this myself, though want to help. Any switches in BIOS that could write-protect your drive? Maybe jumpers in wrong places on this drive or damaged cable?

If you can, get some bootable CD with disk tools and check your drive (chkdisk may be just failing to repair, but hopefully other tools won't).

Also, any strange sounds from this HDD? There is a chance it is just got corrupted.

> **skoberlink said:**
> in addition to the last question my first idea is to copy all the program files etc. over to the linux drive and reinstall windows and and the programs and then copy back in the program files to get my settings, thunderbird e-mail accounts, etc. back. Will that work?Well, it **should** work. However, some apps store config in registry, so you also have to run regedit (or something like that) and export your HKLM & HKCU keys from there.

---

### Post by skoberlink on 2008-06-02
as it turns out none of it matters.  the MFT itself is corrupted so it can't even run chkdsk to just check the disk let alone actually repair anything.  I suppose all that's left is to wipe it and reinstall.  There weren't any personal files that I don't have other copies of.  It was loaded with music but other than that just programs, drivers, and one game so I'll have to reinstall all of that which kinda sucks.  I wish I knew what happened though...

---

### Post by breakthrow on 2008-08-29
Hi,

If you would like to fix this problem using windows then you will loss the data. So first make a backup copy of program files and other data using Stellar phoenix [Linux data recovery]("http://www.data-recovery-linux.com") and then fix it installing fresh copy of windows OS or ubuntu

Hope this helps
Thanks

---

