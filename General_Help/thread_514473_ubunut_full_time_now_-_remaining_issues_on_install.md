---
title: "ubunut full time now - remaining issues on install"
date: 2007-07-31
forum: General Help
---

### Post by bwethington on 2007-07-31
Hello!

I am returning to Ubuntu after a bit of a lay off, and have recently installed 7.04 on my work laptop (Acer TravelMate 8200) and have installed WinXP through VMWare Workstation rather than dual boot (makes it easy very easy to snapshot and backup the entire system, and keeps it nicely contained, plus I can flip back and forth), as I do still need it for AutoCAD, Sketchup, and Adobe products (Need CS2).  They actually run quite well through VMWare on dual monitors, btw.  I made the switch because I got tired of the bloated WinXP that was taking 12-14 minutes (and I timed it) to get from button push to being able to open a program.  It now takes less than 45 seconds.

I started toying with Ubuntu on the Warty distro, and have futzed with linux/unix systems on my NSLU2 and Nokia Internet Tablets, as well as running 6.04 server at home (though I had to give up on that one due to some file sharing problems that I spent WAY to much time working with...I'll probably revisit with 7.10).  So, I have some experience with it all, but I have some little nagging problems I was hoping someone could help me with:

1. Firefox: I have a kind of goofy problem.  When I shut down the laptop, take it home, open and boot to a wireless connection, Firefox refuses to open.  It'll act like it is trying, but it just stops and closes.  If I open Opera, it works fine, but I use Firefox so it is kind of annoying.  If I plug in my backup ethernet, I can open Firefox, unplug the ethernet and then it stays open and works fine from then on.  Not a huge deal, but if I have the same problem while trying to get on to a wireless network in the airport, I am SOL.  Any ideas?

2. backup: Here is what I want to do, and any suggestions are appreciated - 
a. Create a restoration image of the linux partition, excluding my /home directory (which includes my Virtual Machines).  This is really only for disaster recovery, and I plan on creating a SystemRescueCD to be able to restore this image.  I am planning on using Partimage 0.6.4 for this task.
b. Create an incremental backup of my /home /bin /dev and /etc directories that will run at scheduled times (this really should be a core ability on ANY OS, and is one of the glaring holes in Ubuntu, IMHO).
 - Are there other, better programs for restoration images?  Partimage seems to work, but as every other backup solution out there, it isn't very GUI friendly.  I wanted to use backuppc, but I couldn't get it to install and the installation pages I saw were perfectly useless.  Mondo?
- Can anyone recommend incremental backup solutions?  Something that if I have deleted a file, or something goes corrupt, I can simply browse through the archive and restore a single file to a designated location?  Again, backuppc seemed to have promise, but I can't get it to install per instructions I've found.  I realize that I could go through and find or create backup scripts for rsync or tar, but what a pain.  

I have a pirated copy of Acronis 8 that I could use, but I'd rather not...I just want a decent FOSS program with a decent graphical user interface that backs up my files to another drive that I can occasional restore if I have to...is there one out there?  Backup Exec worked pretty well, as did Acronis True Image, and I'll pay for something if I have too, but I rather keep it open source if at all possible...just because..

3. beryl on ATI x1600; Anyone find a solution for this yet?  I'd prefer to use the ATI drivers because my dual screens work just fine and I am afraid to hose it by going to the non-ATI drivers.  Not a biggy, though...

All in all, pretty small problems, but I appreciate any feedback.

Nice to be back :).

bw

---

