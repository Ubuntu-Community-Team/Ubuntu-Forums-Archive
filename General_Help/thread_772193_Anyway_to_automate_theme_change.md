---
title: "Anyway to automate theme change?"
date: 2008-04-28
forum: General Help
---

### Post by Islington on 2008-04-28
I have a unique problem, I have 2 themes, one is light the other is dark, I have customized both to my liking and saved them in the gnome-appearance-manager as A and B.

I like to use the dark theme at night and the light theme during the day. IS there anyway that this change can occur automatically depending on the time of day? even cooler if based on the sunset time. Its not that I mind changing the theme, it takes less than a couple of seconds, but it would be nice if it could be automated.

---

### Post by justleen on 2008-04-28
hmmm intresting..

possibly, yes... you could have 2 folders, A and B, with config files. A third folder - REAL - would contain the actual files used by gnome (eg. ~./themes/) 
then you could run a cron job, coping file from A to REAL at the proper time. the same for the B folder.

Problem is.. how to apply those settings. wouldnt want to do a ctrl-alt-bkscpace in the middle of your work..


edit: maybe its not THAT simple

---

### Post by ryanhaigh on 2008-04-28
I would check whether gconf-editor holds the information about the theme currently in use, I know you can set gconf keys from the commandline, so you could use at or cron to set the theme using gconf. From my experience gconf entry modifications generally take effect immediately.

EDIT: found the tool you need to use to set the gconf keys: [http://linux.die.net/man/1/gconftool-2](http://linux.die.net/man/1/gconftool-2) and here is a howto: [http://ubuntuforums.org/showthread.php?t=392587](http://ubuntuforums.org/showthread.php?t=392587)

---

### Post by vishzilla on 2008-04-28
In Synaptic search for "theme switch" and see what comes up

---

### Post by justleen on 2008-04-28
clicking away for a few minutes:

hmmm gconftool seems to be the way.. 

hint: use gconf-editor to find the different paths / objects

---

### Post by Islington on 2008-04-28
This is why I love you guys.

---

