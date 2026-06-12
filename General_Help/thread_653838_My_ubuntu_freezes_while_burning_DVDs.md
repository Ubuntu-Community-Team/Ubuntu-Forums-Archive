---
title: "My ubuntu freezes while burning DVDs"
date: 2007-12-30
forum: General Help
---

### Post by NiksaVel on 2007-12-30
Hey all,

some1 pls help me out... I've never experienced a problem like this b4... I have pulled myself together a new comp made of old parts which seems to work perfectly with ubuntu, but I have only one problem... when I attempt to burn a dvd, approx. once in 3 burns, the system hangs right after it starts burning. The system is not frozen, just VERY unresponsive - there's a 20 sec lag after tryng to move the mouse and such. It doesn't respond to ctrl+alt+bkspc or ctrl+alt+f1... I've tried leaving it to burn the disk for 1.5 hrs but nothing happened... drive was still spinning like crazy and computer experienced the same symptoms. All I'm left with is hard reboot and reloading with a messed up disk which I have to throw away. I've already messed up 15 dvds  :(

I can vouch that the burner itself is functional, as I was using it for months in my other computer with no prob whatsoever. I've tried k3b, gnomebaker and brasero with same results.
Computer is Athlon 1600XP /w 512 RAM, running daryna.

Some1 please help me out, this is really starting to freak me out!

What I noticed so far is that after a fresh boot the first disk always burns fine, than the second or third freeze up the system.

the burner is LITE ON DVDRW LH-20A1P with the latest firmware... it's a 20x dvd burner, although I've never seen speeds above 10x


PLEASE HELP!!!

---

### Post by markharding557 on 2007-12-30
check if dma is enabled because this can cause burning problems
in a trminel type
> sudo hdparm -i /dev/hdc orwhatever your cd burner drive is
there should be an atarisk agaist udma2 in the udma line
if it is not enabled then type
> sudo hdparm -d /dev/hdc
this will enable dma

---

### Post by NiksaVel on 2007-12-31
it is enabled by default. I've tried turning it off since a friend suggested it might be the cause of problems, but that got me down to burning at 1.5x - which is not a solution...

---

### Post by sliPrix on 2008-01-22
Has anybody figured this out?   I am having the same problems as you, however my first disc fails like your second or third ones do.  I know the drive works as when I flip over to the XP side of my drive, the iso I am trying to burn burns flawlessly.  I am using the built-in burner that comes with gnome, and have burned several discs that have worked in the same manner before, however suddenly, I am unable to do this.  I also tried gnomebaker with the same results.  My whole computer becomes extremely slow and I am forced to reboot.  I also upgraded my firmware on the drive too, and that did not fix my problems.

---

### Post by sliPrix on 2008-01-22
Strangely, it seems that the iso I was trying to burn was made in such a way that Ubuntu just didn't like it.  I made another copy of the disc I was trying to backup by setting the program settings to default (this was in XP).  I then booted back into Ubuntu Gusty and double clicked the new iso I made and not its seemingly working.  Weird stuff, I would still like to know the actual cause of this.

---

### Post by NiksaVel on 2008-01-23
My problems are related to a known bug in the latest kernel regarding certain hardware combinations...   it's well documented, so I simply changed my burner for another model and all is well...

---

### Post by !nkubus on 2008-07-20
> **NiksaVel said:**
> My problems are related to a known bug in the latest kernel regarding certain hardware combinations...   it's well documented, so I simply changed my burner for another model and all is well...


I'm Having the same Issues, where did you find documentation of this problems ?.

I had a LITEON who was burning ok for the 1 CD, and then the "IDE BUS" was freezing.

I changed it to a LG and now I can burn 2 or 3 CD but now the Whole system freeze.

Any links to that bug would be appreciated thanks :)

---

