---
title: "[SOLVED] intel x3100/965: failed to start X server, no GUI at all"
date: 2007-10-11
forum: General Help
---

### Post by Diavo on 2007-10-11
Hey guys,
I Just got a new laptop, a Gateway ML6720, and tried to install Ubuntu Feisty (I'll have limited use for Vista... ever! but still dual boot...).  I had to use the Alternate CD to do so because I got the "Failed to start X server" error which wouldn't let me get into the LiveCD at all.

I've spent the past 3 days searching these forums for that error and possible solutions.
The issue is clearly caused by my graphics card: an Intel X3100, aka the 965.

My new laptop cannot get online, so any files to be installed must first be downloaded onto another computer of mine (or at work) and copied from a USB jumpdrive.  I found instructions on doing that via command line, as well as using "dpkg -i" to install .deb files.

Furthermore, because of this error I cannot get any sort of GUI up at all -- I'm stuck at the CLI after the "Failed to start X server" error.


I downloaded and installed "xserver-xorg-video-intel" (version 1.6.0?) and via "sudo dpkg-reconfigure xserver-xorg" I selected "intel" and went from there, but no dice.  No other setting works either, not even the "vesa". =(

I downloaded and installed 915resolution, ran it with the "-l" param.  It recognized that I've got an Intel chip, but couldn't recognize which, and therefore I couldn't do the MODE= changing trick because it didn't list any modes. =(


Summary:
Ubuntu Feisty installed via Alternate CD
Dual booting Vista
Intel X3100 graphics card (aka 965)
"Failed to start X server" error
Command line interface only =(
Linux newbie

Help!!   Please?  ':-)

A month ago I installed my first Linux distro onto my old laptop: Ubuntu Fiesty.  I really love it.

Thanks for any help anyone can provide!   I read somewhere that the next version (released next week!) should be supporting my gfx card.  If there's no fix, can I just wait a week and install 7.10 and it'll work?
--Diavo

---

### Post by Doo Doo on 2007-10-11
I think your best bet is to just save yourself the headache and try using the gutsy beta it looks like your video card is working under gutsy.

if you really want to get it working with feisty you might want to take a look at this thread.

[http://ubuntuforums.org/showthread.php?t=494943](http://ubuntuforums.org/showthread.php?t=494943)

---

### Post by Diavo on 2007-10-11
Thanks for the reply.  I may just have to do that...

---

### Post by Diavo on 2007-10-23
Various online workarounds never worked for me.  However:
Installing Gutsy Gibbon gave me the GUI! =)

Now the only issue is that the top and bottom system bars don't extend all the way to the edges, and my screen rez reports 1024x786 instead of 1280x800 (widescreen).
"915resolution -l" said it knew I was using an Intel, but couldn't determine which.

Solution? :-|

---

### Post by Diavo on 2007-11-15
This thread solved my desktop gfx problem, giving me the correct rez. =)
[http://ubuntuforums.org/showthread.php?t=610407&highlight=x3100](http://ubuntuforums.org/showthread.php?t=610407&highlight=x3100)

---

