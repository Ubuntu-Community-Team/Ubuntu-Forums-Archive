---
title: "[SOLVED] Gutsy weird behavior after 5 days of joy"
date: 2007-10-25
forum: General Help
---

### Post by tagrace on 2007-10-25
I've been running Ubuntu since Edgy. Upgraded  to Gutsy last week and with only a few minor glitches had it up and running without a problem.

Yesterday I had to shutdown, loaded XP to run a program under Windblows, shutdown and rebooted to Gutsy.

First thing I noticed is that after entering my password, the Bongos played twice. Never did that before.

The system came up looking normal. Firefox opens and I can browse but once I shut it down I can do nothing else other then rotate the cube.

Rebooting get double Bongos and I can open some apps only once. Other apps will not open at all.

I can Ctl+Alt+F2 at any time and have found nothing wrong.

The system was running perfectly prior to the reboot. I installed all updates but did not reboot till now.

I'm not an expert but I just can't find anything wrong.

Any ideas how to get this back to right?

Ted

---

### Post by snickers295 on 2007-10-25
I'm not for sure but i think the upgrade process is bugged up because when i upgraded to 7.10 everything was messed up because the resolution was wrong and i couldn't fix it, no programs worked etc... after a while of it working fine. i would suggest if to download a new CD and do a fresh install like i did because after i did everything worked like a charm.

---

### Post by tagrace on 2007-10-25
I was hoping to avoid a fresh install if possible.

It's just strange that after 5 days of running great it falls on it's face.

---

### Post by tgalati4 on 2007-10-25
It's not strange if you performed some kernel-related updates in the meantime, but did not reboot.  When you reboot, you are running new code, which is subject to new problems.

From your post, it's not clear if you were running Feisty for 5 days and then choked on Gutsy or if you updated successfully to Gutsy then added some more updates before rebooting.

---

### Post by tagrace on 2007-10-25
I was running Feisty since it came out.

I upgraded to Gutsy on Oct 18th and have been running it without problem till yesterday.

I have made no changes to the system manually in the last four days. Only updates via the Update Manager were made. No reboots were done unless required by Update Manager.


Ted

---

### Post by eldragon on 2007-10-25
what i would first suggest is to disable compiz (since you talked about rotating the cube)

i had a minor glitch today which relates to what you experienced........everything was un accesible (mouse / keyboard) except for desktop switching.......slapped compiz with kill and back in biz. :)

---

### Post by snickers295 on 2007-10-25
> **eldragon said:**
> what i would first suggest is to disable compiz (since you talked about rotating the cube)

i had a minor glitch today which relates to what you experienced........everything was un accesible (mouse / keyboard) except for desktop switching.......slapped compiz with kill and back in biz. :)
That make good sense.
i have never liked big eye candy like compiz and beryl and stuff like that because all i use my computer for is e-mail, internet, programming and so i can say "I don't use winblows".
the first Linux distro i have ever used was SUSE Linux 7.10 last year and it wasn't pretty.

---

### Post by tagrace on 2007-10-25
Killed compiz, still no joy.

I think there is a clue here with the playing of the bongos TWICE after entering the password at login. The system never did this before and all the trouble started when the double bongos started. I just don't know where to look to solve this.

---

### Post by snickers295 on 2007-10-25
back up your impotent files and reinstall and maybe that will help.
unless you used some kind of program that might of touched the disk in windows.
sounds like maybe a file has gotten corrupted.

---

### Post by tagrace on 2007-10-25
The windows program program I used does no disk access but who knows what XP did without my knowledge. Windows and Ubuntu are on two seperate hard drives. It is suspcious however, that the problem happened after going to Windows.

I really need to backup some email files before re-installing. I'll do it tonight and re-install tommorow.

The reason for the double bongos is driving me nuts.

---

### Post by snickers295 on 2007-10-25
OK, good luck to you and remember... in a Linux world with without fences and walls, who needs WINDOWS and GATES.

---

### Post by tagrace on 2007-10-26
Ok, here is where I am...

After some research (as if I knew what I was doing) I came to the conclusion that something was not right with the startup xscript. I ran gdmsetup and change the Default Session from xscript to Gnome and guess what. I'm back to normal.

I only get one set of bongos at login and the system seems perfect with compiz and all.

When I get some time I'll look into why the xscript thingy was not working.

Ted

---

### Post by snickers295 on 2007-10-26
thats great!
hopefully you can find out what was wrong with the xscript and get everything back to normal.
good luck.


p.s.
if your problem is solved please mark it as solved in the thread tools.

---

### Post by tagrace on 2007-10-26
Thanks. I'll mark it resolved when I figure it out, or, when I find it over my head.

Ted

---

### Post by dimbulb1024 on 2007-10-26
I had some problems also with the upgrade. After a couple days I lost sound, coming back from suspend was wacky, external hd with ntfs not connecting properly,  ect ...
I just ended up do a fresh install and have not had any issues since.
Taught me to do a fresh install from now on.

---

### Post by snickers295 on 2007-10-26
i think that the upgrade is buggy somehow because mine didn't work and had similar  problems as most people that the upgrade didn't work for but a fresh install does.

---

### Post by tagrace on 2007-10-29
I've marked this thread as SOLVED even though I have no idea what happened.

Synopsis:

I used the UPGRADE to go from Fiesty to Gutsy. All was well for few days but did not do many re-boots.

After a reboot because I had to use Windows against my will, Gutsy was a mess.

I got back to what appears to a perfectly running system by using GDMSETUP and setting it to GNOME instead of XSCRIPT.

The system is running great and it's time to move on.

Thanks for your help. :D

Ted

---

### Post by snickers295 on 2007-10-29
anytime, anytime.

---

### Post by MariusSilverwolf on 2007-10-29
Can you back up your /home directory and any configuration specific files from /etc you might need before running a fresh install?

Best guess for it playing the bongos twice is that part of the user environment structure is being loaded twice, which results in command conflicts when you try to open/close apps.

{edit -- Whoops, missed the second page somehow!  Glad you got something resolved, even if root cause is still unsdiscovered.}

---

### Post by tagrace on 2007-10-29
If someone can point me in the right direction to to find and decipher the  xscript that is (was) running on startup I'll be happy to look at it and try to figure out what happened. I'm not totally "programing challenged" but Linux is fairly new to me and I don't know all the in's and out (yet).

What file am I looking for is the question?

Ted

---

### Post by tagrace on 2007-10-29
I just read in another thread that the default x script just runs the Gnome startup. There must be something in that default x script that is not correct. Anyone know where it is and what it's called so I can look at the script?

Ted

---

### Post by stoodleysnow on 2007-10-29
I tried the Upgrade first. made a total mess, similar to your description, only it happened straight away. Install straight from the cd and everything will be ship-shape before you can say "this is an unnecessary thing to say, why am I saying it?!"
:guitar:

---

