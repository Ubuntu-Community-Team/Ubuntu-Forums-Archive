---
title: "sound only works for some things"
date: 2006-11-21
forum: General Help
---

### Post by Preserved Killick on 2006-11-21
Hi.  I hope someone here can help me diagnose and correct this problem.  I'm not a newbie to Linux, but I've never had to correct a sound problem before, so I need some basic help.

Sound works when I play an ogg file with totem.  I get system sounds when I login.  I *no longer* have sound in bzflag (a game) or in Firefox flash at places like YouTube, though this used to work.  Softsqueeze (a java program that streams media from Slimserver) won't turn on.  I can start Softsqueeze, but it gets no data from the slimserver.  I have no idea if this is part of the problem or not.  It also used to work flawlessly.  Slimserver can still stream ogg and mp3 to other devices on my network without a problem.

The only things I can think of that may have caused these problems is eihter a power failure that occurred shortly before I noticed these problems, or maybe one of the almost-daily Ubuntu updates.  I recently re-installed slimserver, but sound worked after that step, so I don't suspect that is the problem.

I have two sound cards, which show up when I type in lspci

0000:06:01.0 Multimedia audio controller: Creative Labs SB Audigy LS
which I had added and:
0000:00:1b.0 0403: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 03)
which was built in to this system.

When I click on System > Preferences > Sound, it shows HDA Intel as the driver.  I can select ca0106 instead (the driver for the Audigy card) but when I close this window, it doesn't stay selected.  When I look again, it shows up as HDA Intel.

If I right click the sound icon on the gnome panel, and play with the volume control preferences, I can select CA0106 (Alsa mixer).  Or HDA Intel. It seems to make no difference.

If I run alsamixer at the command line, it indicates it is running CA0106.

It would be good if I could find out:
1.  Which sound card my system is using (or which one for which apps)
2.  What Linux sound system is my system using (alsa or something else?)

Anyone know what to do on this partial muteness problem?

Thanks,

Preserved Killick

---

### Post by Preserved Killick on 2006-11-22
OK, I don't know what started this problem- maybe an update killed something, I don't know.  But I have solved part of the problem.

I used synaptic to install alsa-oss, an "alsa wrapper" that lets programs running a different sound method than alsa work with alsa.  (Picture alsa developers cringing at this explanation).  Anyway, if I put aoss before the command to start BZflag, then sound works in bzflag. e.g.

$ aoss bzflag

This same technique does not get sound working in firefox flash, though.

Anyone know how to get sound working in firefox flash?  Thank you,

-- Preserved Killick

---

