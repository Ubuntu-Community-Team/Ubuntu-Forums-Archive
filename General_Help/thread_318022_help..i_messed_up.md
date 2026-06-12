---
title: "help..i messed up"
date: 2006-12-13
forum: General Help
---

### Post by paccman on 2006-12-13
hi all...
i am a biigg noob to linux but i am wanting to learn and try.   i have a old box with about 200megs ram and an old amd k63 chip , it has 2 hard drives...i disconnected the first hard drive with xp on it so i could install ubuntu to the second hard drive and then wanted to try the dual boot method using the f8 key to switch between the two drives....needless to say i was way over my head and trying things i should have waited to try later once i learn more...so it ok to laff at me now ....there was some issue i cant identify but never was able to get ubuntu to load up with or without the f8 key and have now decided to put the generic desktop version on the back of another and larger hard drive where the computer is newer and able to just use lilo or whatever to access ubuntu and still be able to switch to win xp as it will be the main os i use until i learn more about ubuntu...my question now that ive gone all over this is that i would like to get the version of ubuntu off my old computers second hard drive...i re hooked the primary hard drive in with xp as the master and it boots great and i can see the second hard drive in windows explorer...but i cannot get ubuntu off and have tried to use xp to just format the drive so i can use it to hold old data ..( this computer will not be fgoing vback online as i plan to use it to do my bills and save my resumes and such but if i cant get ubuntu off this drive nad get it back to a formatted version where windows will let me put data on it...its a wasted hard drive for  now..any suggestions on maybe a way to fdisk the hard drive or format it to rtemove ubuntu for the time being?....again im not giving up i just will put the simple desktop version on the vback of another computer so i can learn to use this awsome product...but for right now i need to get my old hard drive back...the bios sees the hard drive and xp sees the hard drive but i cant get it to format so i can use it as a back up with xp....ther must be some way to uninstall it and then get xp to format this disk so i can reuse it for data storage.....then i will like i said put ubuntu on another computer with a small partition and start using it to learn on...plz help...there must be a way to get the install of this old hard drive...like i said i can see the hard drive in xp and in bios but cannot access the drive or get it to format with xp or even using old floppy win disk to fdisk it or format it...plz any help would be appreciated...thanks in advance for any advice....pacman/mark

---

### Post by hikaricore on 2006-12-13
Mark you do realize that by chaging the boot order of the drives:

Ie: Unhooking one to install ubuntu, then plugging it back in.

That you're pretty much installing a boot loader on a drive that your system is not booting from and have no chance of ever getting ubuntu to launch.  Why are you hitting the F8 key?  Grub doesn't use the F8 key, the windows bootloader (which can not load linux) uses the F8 key.

Anyway moving right along.  If you're using a hard drive over a certain size, sometimes windows can't and won't try to give you the option of formatting it.  You may need to track down the maker of this hard drive and download their formatting tool specailly designed *blah blah* for their hardware.

---

### Post by Iowan on 2006-12-13
Guess I haven't gotten used to XP's new way of doing things.
I can't seem to get **fdisk** to work. I did discover the **DiskPart** command - which seems to do what **fdisk **did.

---

### Post by paccman on 2006-12-13
i know i really messed up, like i said i was doing things way over my head and knowledge base...and understand that most of you will want to laff as i should have just stuck to the basics...my fault...but if someone knows how i can rformat the hard drive so it is clean i sure would appreciate it...the hard drive works ok, but even if its plugged in alone i cant seem to get it to format...help...please and thanks again](*,)

---

### Post by hikaricore on 2006-12-13
I told you where to start looking, if you're too lazy to find out if your hard drive manufacturer offers a formatting tool for their drives well then I can't really help you.

---

### Post by igknighted on 2006-12-13
try formatting via the Ubuntu live CD or downloading the gparted live CD, they both have excellent formatting tools.

As for the dual boot... before wiping your drives clean, try changing the boot order in your bios to boot the Ubuntu disk first, then add Windows to your GRUB bootloader.  This should enable the system to boot fine... once you get Ubuntu booted post back for help with grub.

---

### Post by paccman on 2006-12-13
no no no..sorry if i sounded ungrateful....i was at workand was unable to look up the hard drive this morning...i appreciate the adice and am looking up the drivers and suppoort issues this evening..i wasnt being lazy...i just wanted to confirm that i really made a mess and made such a dumb mistake....again i thank you for your advice i am far from lazy tho and that was a bit rude to say such when you havent even taken into consideration i was just trying to be friendly and admit my own stupidity...but thank you again never the less...i hope i can find a utility at fujitsu for such an old drive...we shall see...if not , im open to other suggestions too...thanks again:???:

---

