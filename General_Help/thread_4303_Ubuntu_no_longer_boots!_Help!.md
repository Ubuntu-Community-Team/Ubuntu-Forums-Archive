---
title: "Ubuntu no longer boots! Help!"
date: 2004-11-13
forum: General Help
---

### Post by Termina on 2004-11-13
After ubuntu froze while I was playing a game, I restarted it to be greeted by this error message:

Starting Ubuntu...
hda: timeout waiting for DMA
hda: drive notr eady for command

I'd rather not have to reinstall Windows 2000, and I was satisfied with Ubuntu until this happened. =/

Any help?

---

### Post by zenwhen on 2004-11-13
Mama mia! Thatsa Deada Harda Drive!

---

### Post by Termina on 2004-11-13
This does not seem to be the case, since I can access both hda1 and hda2 (ntfs/linux partitions) on the hard drive that is "dead". =/

Any other ideas?

---

### Post by FLeiXiuS on 2004-11-13
[QUOTE=Termina]This does not seem to be the case, since I can access both hda1 and hda2 (ntfs/linux partitions) on the hard drive that is "dead". =/

Any other ideas?[/QUOTE]

Usually what I do to fix this sort of problem is just turn off my computer for a several hours, then it usually gets all of the bugs out.  Fixes a lot of problems for me.  Give it a shot.

---

### Post by Termina on 2004-11-13
I'm unsure if you are joking or not in both of your posts, or being stupid on purpose.

I'm quite sure this isn't going to fix the problem. ;-_-

Thank you for your "help", but if this is the level of intellegence it takes to be a mod on these forums, I'm probally better off at linuxhelp.ca/forums

---

### Post by allen on 2004-11-13
[QUOTE=Termina]I'm unsure if you are joking or not in both of your posts, or being stupid on purpose.

I'm quite sure this isn't going to fix the problem. ;-_-

Thank you for your "help", but if this is the level of intellegence it takes to be a mod on these forums, I'm probally better off at linuxhelp.ca/forums[/QUOTE]
 have you tried a complete power down ?

ie. power plug switched off instead of just a shutdown.

---

### Post by TravisNewman on 2004-11-13
[QUOTE=Termina]I'm unsure if you are joking or not in both of your posts, or being stupid on purpose.

I'm quite sure this isn't going to fix the problem. ;-_-

Thank you for your "help", but if this is the level of intellegence it takes to be a mod on these forums, I'm probally better off at linuxhelp.ca/forums[/QUOTE]
 Dude, no offense, but if you insult the intelligence of moderators on a community forum, you're not going to get much help. Fleixius has always been helpful, and in my experience in this case, sometimes powering off for a few minutes (I dunno about hours, but...) does fix a lot of things. Completely pull the power cord out of the back for about 15 minutes to let the power get out of everything and then start it back up and see what happens.

---

### Post by FLeiXiuS on 2004-11-15
[QUOTE=panickedthumb]Dude, no offense, but if you insult the intelligence of moderators on a community forum, you're not going to get much help. Fleixius has always been helpful, and in my experience in this case, sometimes powering off for a few minutes (I dunno about hours, but...) does fix a lot of things. Completely pull the power cord out of the back for about 15 minutes to let the power get out of everything and then start it back up and see what happens.[/QUOTE]


Thank you for your support.  And by the way, Yes powering off the machine fully gives the hard drive time to spin down therefore fixing and buffering problems which may result from a hard drive crash.  Please don't insult nor dis-credit our abilities.  We do know whats best.  Well most of the time  :grin:  :wink:

---

### Post by jdodson on 2004-11-15
[QUOTE=Termina]This does not seem to be the case, since I can access both hda1 and hda2 (ntfs/linux partitions) on the hard drive that is "dead". =/

Any other ideas?[/QUOTE]

ok first off, please dont insult the forum moderators or any other user, flexius is helping you out of his own free time, as is the rest of the community, please show respect as we are all human beings.  please understand the philos. of ubuntu:

```
"Ubuntu" is an ancient African word,
 meaning "humanity to others".
 Ubuntu also means "I am what 
I am because of who we all are".
 The Ubuntu Linux distribution 
brings the spirit of Ubuntu to the
 software world.
``` 

i have had problems like you describe.  i think you harddrive is going bad.  i have had some sectors go bad while others are fine, rendering the machine unbootable to linux.    this is because certain sectors that contain the kernel or bootloader have gone bad.  this has rendered one of my harddrives unusable as i cannot read the first few blocks thus making it impossible to install ANY os on the drive.   depending on the harddrive you can download a tool(i know western digital makes them) to analyze your drive for unfixable or fixable errors.  most drives come with only a one year warranty, which bites.  though remember that your harddrive spins all the time, the only other hardware in your computer to move as much would be the CPU fan, unless i am forgetting something else, usuage causes wear on ANY component.  

to track off on a different subject, i remember awhile ago people used to recommend to leave your computer on and never turn it off.  i could never figure out why this was.  power consumption is one thing that comes to mind.  second is that computers are not machines that can be run forever and never break from wear.  at times things simply wear out or go bad.  thus is the way of life with the assembly line proccess of the industrial revolution.

ok getting back on track, i would (ASS)ume it is unfixable, but i have been known to be wrong on a daily basis :wink:

---

### Post by FLeiXiuS on 2004-11-15
[QUOTE=jdodson]but i have been known to be wrong on a daily basis :wink:[/QUOTE]

Haven't we all?  

If that doesn't work for you, i'd try downloading a program to ZERO the whole entire drive.  That usually fixes any problem :-).  Zero basically turns all of the HASH values on the drive to strings of 0000.  Thus, no data is left nor partitions.

---

