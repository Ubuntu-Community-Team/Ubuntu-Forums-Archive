---
title: "Should I format?"
date: 2008-01-23
forum: General Help
---

### Post by Ertai87 on 2008-01-23
So, my Ubuntu's been acting a bit weird pretty much since I installed it.  Having come off a really hard time with Windows, this is a bit unsettling.  All the problems seem to be resolved, but I'm wondering if these problems are resulting from Ubuntu not being "licensed" software and thus not running proper drivers for my hardware (my hardware works, but they're not "official" drivers or w/e), or if there's something wrong with my install.  Here's my hardware setup, along with some of the things I've encountered:

Dell Inspiron 6400
Integrated A/V
Broadcom 4311 Wireless GFX card
1 GB RAM
DVD/CD-RW drive
Video running natively at 1200x800, through external monitor at native 1680x[something else]

1) My CD-ROM drive mounted twice on boot if there was a DVD in the drive on boot.  I found a solution to this online involving changing my fstab file, which I did, but it happened a couple times after that.  It hasn't happened for the past day or so, so I think it's been resolved (it used to happen with roughly 80% frequency). - NOTE: THIS ISSUE HAS REAPPEARED.

2) Randomly, all my Firefox cookies got erased.  I have no idea why or how; I just booted up my comp one day and it was gone.  I doubt I triggered anything (I didn't clear private data or anything like that; I would have remembered doing something like that).  It's only happened once though, so it could have been me doing something else dumb.  If anyone has an explanation aside from me being dumb that might shed some light, please share.

3) My Wireless card randomly turned off once.  Again, I attribute this one to me likely being dumb, as I was hitting the standby and hibernate keys quickly, which are close to the "turn wireless on/off" key.

4) I found a bunch of items in my IPTables that I didn't put there.  Most of them are "drop" items, so I'm not concerned.  I attribute this to Firestarter, but I'm not sure.  I really have no use for Firestarter, so does anyone know: if I uninstall Firestarter, will it get rid of its entries?

5) I have a zombie process running on my system that shouldn't be there.  Having uninstalled the program and then reinstalling it, the process went away after uninstall, so I doubt it's malicious.  I attribute this one to uninstalling a default "run-on-boot" application that Ubuntu comes with, hence boot procedures stopping prematurely.  The program I uninstalled was vino, since I have no use for RDP.  Is this a likely cause?

6) Lastlog didn't work.  I fixed it by running lastlog in no-X mode, and since then it's worked.

7) Sometimes on boot if I boot without plugging in my external monitor first, it screws up the alignment of my screen once I log in.  This is usually fixed by a reboot.

So, given these issues, which is more likely: Ubuntu's Dell drivers aren't up to snuff (and I do things without realizing I've done them), or my computer's been compromised?  Reformatting is a pain, so I'd like to stay away from it if possible, but I'd prefer to format and have a secure computer than be lazy and be unsecured.  I'm still a bit new to the free software thing and know almost nothing about hardware/software interaction (drivers and such), so I don't know what to expect, which is why I'm asking this.  Thanks.

---

### Post by Mikecore on 2008-01-23
If your computer came from Dell with Ubuntu installed. I Don't thinks its Ubuntu even if it didn't its been my experience that most time things are pretty stable and if things are not you will know whats up just by reading the forums because everybody is having similar issues. I would reformat and change all your passwords It kinda sounds like your box might have been owned. If not reformatting isn't going to hurt and its can put your mind to rest.
Plus it might help solve your problems.

---

### Post by Ertai87 on 2008-01-23
Nope, my comp came from Dell with Win XP Media Center installed.  The Ubuntu install I got came from a live CD.

If I do have to reformat, is it safe to keep my ~ directory (i.e. copy it to an external hard drive and then copy it back)?  I have a lot of stuff in there I'd like to keep...

[edit] A bit of a clarification on the CD-ROM drive problem: It's kind of hard to explain, but I'll do my best.  Basically, what would happen is I would get 2 shortcuts to my CD-ROM drive on my desktop on boot, both linking to /media/cdrom0.  If I ejected the CD, one of the icons would disappear, but the other wouldn't.  Upon opening that shortcut, it would open /media/cdrom0 as an empty folder.  Upon re-inserting the CD, it would replace the second shortcut but not delete the first.  If I inserted a CD after the computer was booted, there was no problem.  My BIOS boots from the CD-ROM drive as primary source; could that have been part of the issue?  Also, this issue happened since I first installed Ubuntu, so it wasn't something that just started randomly.

---

### Post by Mikecore on 2008-01-24
First off your BIOS doesn't boot off your cdrom drive. I think what your trying to say is your first boot option is your cdrom ( right? ). Second you could back up your home folder but I wouldn't. what ever you need ( pictures, file, games ) I would save to a cdrom or dvd but don't just copy your ~ folder there are hidden config files that might or could mess up your new install.

---

### Post by Ertai87 on 2008-01-24
Right, that's what I meant.

As for backing up, I was going to back up personally-created files (visible files in ~ and non-hidden subfolders), plus .wine (wine games) and .mozilla (passwords and stuff).  Of course I'd stay away from touching stuff I don't know.  Those files should be OK though right?

---

### Post by Mikecore on 2008-01-24
> **Ertai87 said:**
> Right, that's what I meant.

As for backing up, I was going to back up personally-created files (visible files in ~ and non-hidden subfolders), plus .wine (wine games) and .mozilla (passwords and stuff).  Of course I'd stay away from touching stuff I don't know.  Those files should be OK though right?

If you think your box might have been hacked I would change "all your passwords" and save as little as possible. only keep what you absolutely need and them virus scan it before you transfer it back to your box.

---

### Post by Ertai87 on 2008-01-24
Awww man...none of my accounts have been noticeably hacked though...but yeah I understand...

And virus scan?  I thought Linux didn't have viruses...

---

### Post by Mikecore on 2008-01-25
Google "Root Kit" and yes there have been a few. Most problems are fixed the same day they are found.

---

### Post by Ertai87 on 2008-01-25
I use chkrootkit.  It hasn't found anything to date.  Also, my ubuntu is up to date (as of this morning).

---

