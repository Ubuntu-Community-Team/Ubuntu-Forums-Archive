---
title: "[SOLVED] Restore &amp;quot;Factory Settings&amp;quot; to Ubuntu?"
date: 2008-04-07
forum: General Help
---

### Post by King_Critter on 2008-04-07
Due to my incessant tinkering, I've borked my current Ubuntu install so badly that I want to restore all the programs I have installed to their like-new, just downloaded state. "sudo dpkg-reconfigure *" doesn't work, apparently, so is there any other ways of doing this?

---

### Post by tubasoldier on 2008-04-07
```
sudo dpkg-reconfigure --all
```

Before you run this command please wait for someone to verify it. It has been a while since I have run something like that so I'm not quite confident about it. Or google it for more information.

---

### Post by FuturePilot on 2008-04-07
You can remove all the directories in your home folder that begin with a . dot. Those contain all your config files for the programs. Removing them will reset all the setting to default.

---

### Post by sdennie on 2008-04-07
It really depends on how you've broken stuff.  If you've broken applications via bad settings then, yeah, as FuturePilot says, removing all the config files from your home directory will likely fix the problem.  If you've broken things by installing .debs with --force-all or installing stuff from source, your only recourse may be to just re-install Ubuntu.

I can't even count the number of times I've broken my machine due to too much tinkering.  It's almost always at a package level and not an app config level though.  If you do re-install, I would recommend creating a /home partition so that you can freely break your machine, re-install and not lose any real data (always remember to tar up /etc though... ;) ).  My /home partition has lasted about 10 installs of 7.10/32bit/64bit/8.04/etc with no data loss or hassle.

---

### Post by King_Critter on 2008-04-08
Alright, thanks to everyone who replied. Unfortunately, I think vor is correct on this one -- the problems run a bit deeper then configuration problems. Luckily, at least it's still usable, so I'm just going to wait for Hardy Heron rather then reinstalling Gutsy. 

making a separate partition for /home sounds like a good idea -- I think I'll do that this time. Question, though -- what's stored in /etc?

---

### Post by sdennie on 2008-04-08
/etc will contain system level configuration files.  It's useful to make a backup copy of it if you are going to re-install because it's common to make changes to some of those files and it's nice to have a reference of the changes you've previously made to things like /etc/apt/source.list or /etc/X11/xorg.conf.

---

### Post by King_Critter on 2008-04-09
Ah, ok. Thanks for the info.

---

