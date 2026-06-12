---
title: "[SOLVED] Computer w/ 2 Hard Drives, One with Ubuntu, and the other with XP.  Will thi"
date: 2008-06-01
forum: General Help
---

### Post by redonwhite on 2008-06-01
Hello,  Im about 3 days into Ubuntu.  And i LOVE it!  There is only one problem.  Im a hardcore Game Junkie.  So i need XP for my games.  I would like to take this Hard drive ( with Ubuntu installed ) and put it inside my Main Rig.  My main Rig has one Hard drive ( with XP installed ).  My goal is to be able to turn my Main Rig on and be able to choose witch OS i would like to boot.  So that when i want to game i can Boot XP, and when i want to pretty much do Everything else i can boot Ubuntu. Now can i simply take out this Hard drive (ubuntu) and install it into my other computer as a second drive?  Thank you ahead of time for your help and time.

---

### Post by werries on 2008-06-01
yep, totally possible. you will have to reload grub so that it recognizes ubuntu though.
probably using the livecd. i don't remember the exact commands. so someone else should correct me if im wrong before you attempt this, but in terminal
```
sudo grub
find /boot/grub/stage1
```
that should output the harddrive and partition of your ubuntu install. and then replace (hd0,3) in these commands with the output of that:
```
root (hd0,3)
setup (hd0,3)
quit
```
then restart, remove cd, and boot from harddrive. 

Do not follow this until someone else confirms.

EDIT: Also, I run counterstrike source/starcraft/diablo2/WoW all on my ubuntu machine via wine at great framerate. you could do that.

---

### Post by SirPerigrin on 2008-06-01
You would have to reinstall grub to accomplish this in most cases. Theres a small chance you could install the Ubuntu drive as the Primary drive and grub not die, but Ubuntu does a lot of config during install that would be off from your new hardware... Overall its not the worlds best idea. You could put the XP drive in the Ubuntu machine as a slave just fine and reinstall Grub to find XP, but moving linux installs never works out so well.

The biggest problem isn't going to be grub, but config files.

My Personal recommendation is to backup whatever data you have on Ubuntu, write down any instructions for how you tweaked this and that, and reinstall after moving the drive.

---

### Post by redonwhite on 2008-06-01
Thanks for the responses guys.  Now would it be better to just wipe this hard drive completely and reinstall ubuntu on this hard drive after i install the Hard Drive in my Main computer as the second hard drive.  Because i don't mind doing that.  Especially if it means a cleaner Ubuntu on my Main Rig.  As for as the stuff about grub i kind of understand you.  But im very new to this terminal thing.  So far ive only messed with it a little bit when trying to set up synergy.  And in the end it didnt work out to well.  And if you think wiping this drive, then reinstalling ubuntu after the HD is installed on the Main comp as second drive is a good idea,  How would i go about getting the ubuntu CD to Boot from that second Hard drive?

---

### Post by werries on 2008-06-02
yes, yes, a clean install would do nicely.
as for booting the Cd....
just pop that in the CD drive, and during installation, make sure you pick the correct harddrive.
EDIT: I think before the final thing, when it previews, you can go to advanced to see where grub is installing. and i think it might be better to install it to the MBR of the windows harddrive (ONLY THE BOOTLOADER THOUGH). becuase if thats the main harddrive, it would always boot from that. unless you change your boot order in BIOS or something.

Also, I'm only partly linux experienced. a few months. so.. someone confirm again? :)

---

### Post by SirPerigrin on 2008-06-02
Once both drives are in the new machine just boot the install CD and make sure you specify the right drive during partitioning. The installer makes it very easy to do.

---

### Post by redonwhite on 2008-06-02
Oh Great!!! =).  One more question.  Now this one will sound very Newbish =)  Hahahah.  How do i completely wipe this Drive?  And Thanks again for the quick responses guys.

---

### Post by redonwhite on 2008-06-02
Also...  would i still keep the ubuntu Hard drive a master?

---

### Post by SirPerigrin on 2008-06-02
Dont even bother, just leave it as is then let Ubuntu format it on install. formating wont wipe it, but you wont be able to find any trace of what was on it without disc recovery software so works just as well for this purpose.

---

### Post by werries on 2008-06-02
if you choose to use whole disk, it will overwrite... it wont really matter whats under it. don't worry about wiping a disk unless you intend on getting rid of it and for fear of someone finding your data.
but for future reference...
[http://www.killdisk.com/](http://www.killdisk.com/)
that does a nice process to wipe all. dont do it in this instance tho.
EDIT: i am loving how me and sirperigrin are saying basically the same things.

---

### Post by SirPerigrin on 2008-06-02
> **redonwhite said:**
> Also...  would i still keep the ubuntu Hard drive a master?

Ubuntu really doesent care much, so do whatever you feel like. As long as you have 1 master and 1 slave, everything works.

---

### Post by redonwhite on 2008-06-02
haha i like it to.  It makes me feel better to have two people with Linux exp giving me advice.

---

### Post by redonwhite on 2008-06-02
> **SirPerigrin said:**
> Ubuntu really doesent care much, so do whatever you feel like. As long as you have 1 master and 1 slave, everything works.

the hard drive in my main rig (windows xp) is set to master.  so then are you saying i should set the ubuntu to slave then?

---

### Post by werries on 2008-06-02
just come reply and tell us if anything goes sour
edit: yes. ubuntu as slave if windows is master

---

### Post by SirPerigrin on 2008-06-02
> **werries said:**
> if you choose to use whole disk, it will overwrite... it wont really matter whats under it. don't worry about wiping a disk unless you intend on getting rid of it and for fear of someone finding your data.
but for future reference...
[http://www.killdisk.com/](http://www.killdisk.com/)
that does a nice process to wipe all. dont do it in this instance tho.
EDIT: i am loving how me and sirperigrin are saying basically the same things.

lmao, this happens to me a lot... hey, at least we provide two nerds to blame when stuff goes wrong :)

---

### Post by werries on 2008-06-02
hahaha yep.

---

### Post by redonwhite on 2008-06-02
Thanks buddy.  Okay im gonna go give this a wirl.  Hopefully ill be back here thanking you guys through ubuntu in a bit.  =) Thanks again for the help!!!

Over and Out

---

### Post by Unix_Slayer on 2008-06-02
I always tell people to use two hard drives. I never let my Windows touch my Kubuntu drive, except through wine. Good choice my friend.

---

### Post by werries on 2008-06-02
eh, i dual boot on same harddrive. never gave me any problems.

---

### Post by SirPerigrin on 2008-06-02
same, and tbh i dont think i'd do it any other way. Why run each OS on its own drive when you can run those drives in RAID!!!

---

### Post by werries on 2008-06-02
haha, im on a laptop. single harddrive. no RAID for me.

---

### Post by SirPerigrin on 2008-06-02
> **werries said:**
> haha, im on a laptop. single harddrive. no RAID for me.

hehe, so am i, i was merely remarking if i "Had" two drives :) its nice to dream!

---

### Post by redonwhite on 2008-06-02
blahhh.  the ubuntu hard drive is IDE.  My Main Rig only has one IDE input and thats used up for my CD/DVD player.  oh well.  I like S-ATA better anyways.  Ill just buy a small S-ATA Harddrive this week.  Oh well. hehe.

---

### Post by werries on 2008-06-04
alright. lol. enjoy.

---

### Post by Unix_Slayer on 2008-06-04
I think I have bunch of IDE's around. Anyone interested, you pay the freight... and I'll send it off. They are small 40, or 60 gb drives.

---

