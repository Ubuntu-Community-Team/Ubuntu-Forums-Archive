---
title: "Dapper not booting up!"
date: 2007-07-22
forum: General Help
---

### Post by gottatrieit on 2007-07-22
I recently shutdown my computer, but when I tried to start it up the following day, it would not boot!
	
	I am using Dapper Drake 6.06 on an AMD Sempron processor machine with an nVidia video card.  Up until today, I have had no problems with my system like this one.
	The following messages are what appears on the screen just after the [blah blah --- ok, booting the kernel] message:
		
	:17179570.972000: RAMDISK: ran out of compressed data
	:17179570.972000: invalid compressed format (err=1)
	:17179570.972000: kernel panic - not syncing: VFS: unable to mount root fs on an unkown-block (0,0)
	:17179570.972000:   Cursor sits at this point and no input is accepted to the machine; the only way to shut it down is with a hard shutdown!

	Any help will be greatly appreciated as I am still a gNu-Bee at command line stuff and Linux in general.

---

### Post by overdrank on 2007-07-23
> **gottatrieit said:**
> I recently shutdown my computer, but when I tried to start it up the following day, it would not boot!
	
	I am using Dapper Drake 6.06 on an AMD Sempron processor machine with an nVidia video card.  Up until today, I have had no problems with my system like this one.
	The following messages are what appears on the screen just after the [blah blah --- ok, booting the kernel] message:
		
	:17179570.972000: RAMDISK: ran out of compressed data
	:17179570.972000: invalid compressed format (err=1)
	:17179570.972000: kernel panic - not syncing: VFS: unable to mount root fs on an unkown-block (0,0)
	:17179570.972000:   Cursor sits at this point and no input is accepted to the machine; the only way to shut it down is with a hard shutdown!

	Any help will be greatly appreciated as I am still a gNu-Bee at command line stuff and Linux in general.

Hi, I've read in you past post that a week ago you made some kernel changes, could this be part of the problem? Did you make those changes that you referenced in the prior post? If so do you have the still have the kernel options in the grub to where you can choose a boot? If not post back and we will search and hopefully find some help for you.

---

### Post by gottatrieit on 2007-07-24
overdrank,
  Kernel question is sort of; I did change to the K7 kernel but left the i386 still showing. (if that makes any sense; I didn't delete the i386 references).
  Does "grub" come up as part of the boot screen prior to the "ok, booting the kernel message"?
  I noticed in other postings about memory stick problems, so I pulled mine out and cleaned it and the slot it goes into.  No change when I re-booted.
  I live in Florida and we've had thunderstorms every day. My machines are on surger protectors, but the power still fluctuates on occasion during the storms. I make sure they are shut down after I hear the first thunderclap, though. :-)
  The hard drive I'm using is an older 40gb and I've erased it at least 20+ times to install one system or another on it.  It seems strong still but could that be the problem?  I intend to remove it and try it in my "play around machine" (the one I'm using now to post with and scan forums.)
  Question about "grub" is if it's that message string I got when I put in my Dapper disk, I tried to select a different kernel option plus a couple of options, too, but each try failed.
  I printed out a copy of "System recovery with Knoppix" from [www.ibm.com/developworks/linux/library](www.ibm.com/developworks/linux/library) ......., but I couldn't get my "home" files copied to a cd for some reason and I tried to download the newest version of Knoppix and screwed that up somehow, too.
  Sorry I'm so long-winded, but I'm frustrated and want to give you as much info as possible.
  I enjoy Linux and don't want to go back to mickey-stuff, so I'll keep plugging away.  If all else fails, I'll erase the disk and start over, again! lol ;-)

---

### Post by gottatrieit on 2007-07-28
Did it!  Couldn't find a resolution to this situation, so I wiped my hard drive clean and now have a new install of Dapper. Oh well!  I had some stuff backed up on a cd, so it wasn't a total wash-out.

---

