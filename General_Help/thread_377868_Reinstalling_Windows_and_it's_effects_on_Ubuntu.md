---
title: "Reinstalling Windows and it's effects on Ubuntu"
date: 2007-03-06
forum: General Help
---

### Post by venator260 on 2007-03-06
Since my Windows XP seems to be broken, and I have too much crap installed anyway, I'm going to activate Dell's system repair, which will wipe my XP partition clean and reinstall Windows. 

My question is, is this going to mess with the boot manager that allows me to get into Ubuntu, and if so, how do I get it back without reinstalling Ubuntu.

---

### Post by theophane.weber on 2007-03-06
I don't know about the dell software in particular, but I would say that it is likely that Windows will overwrite your master boot record, and you won t be able to boot ubuntu anymore  (i dont think, but I am not certain, that windows will allow you to boot ubuntu without doing something particular) By reinstalling Grub you should be able to boot normally. Backup your ubuntu data, though: it could be that the dell restore plain formats the hard drive. Normally windows asks you on which partition you want to install it. Maybe you should reformat that partition under linux, and then tell windows to install on it
-théo

---

### Post by Jonne on 2007-03-06
Just back up your /home/ folder on a cd/dvd or external hd. Then let the Dell thing do its crap and reinstall Ubuntu afterwards if it's borked. All your settings are stored in /home/ anyway (with the exception of /var/www if you were running a website, or any of the other stuff you needed to use sudo for, but you'd probably know about anything you want to keep outside of /home/).

Reinstalling Ubuntu is painless, especially since you can keep doing stuff while it's reinstalling, and installing an application is literally one click.

Btw: it's a good idea to put /home/ on a seperate partition, that way you can reinstall Ubuntu (or even change distro's) at any time without losing any settings. Ubuntu itself needs a partition of max 15 gig (and that's with a huge margin, on my system it's actually only using 3,70 gigs. If you decide to install everything you can in synaptic, you'll use more than that, ofcourse)

---

