---
title: "Failed to start the X server (after messing with xorg trying to get dual monitors)"
date: 2007-04-25
forum: General Help
---

### Post by charles hp on 2007-04-25
I was trying to follow some on these forums instructions on expanding my desktop across two screens, and I messed up pretty bad it seems. I had just installed ubuntu (7.04) minutes before, so if the easiest way to fix this is to completely replace the data on my linux partition (also running XP on another partition) then thats fine.

Anyway, the screen asks me if I want to "view the X server output to diagnose the problem". when I say "yes", it shows me:

X Window System Version 7.2.0
Release Date: 22 January 2007
X Protocol Version 11, REvision 0, Release 7.2
Build Operating System: Linux Ubuntu
Current Operating System: Linux gateway 2.6.20-15-generic #2 SMP Sun
Apr 15 07 07:36:31 UTC 2007 i686
Build Date: 04 April 2007
[INDENT]*blah blah about checking wiki.x.org to make sure I have the latest version*[/INDENT]
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting, (++) from command line, (!!) notice, (II) informational, (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) log file: "/var/log/xorg.0.log", TimeL: Tue Apr 24 23:37:40 2007
(==) Using config file: "/etc/X11/xorg.conf"
(WW) RADEON: No matching Device section for instance (BusID PCI:1:0:1) found
(**) RADEON(0): RADEONPreInit
RADEONScreenInit c0000000 0

and I'm getting tired of typing nonsensical stuff randomly, so if there are any other particular parts of this huge output that I should post, PLEASE tell me.

Any hope? Looks like I wont get to play around in Linux as much as I would have liked tonight

---

### Post by BoneKracker on 2007-04-25
just replace /etc/X11/xorg.conf with the backup you made before you started dicking around with it
:)

---

### Post by BoneKracker on 2007-04-25
At the top of the xorg.conf file, I believe it has instructions (at least it used to) on how to run a utility that will regenerate the default xorg.conf file for you, even if you've edited it.

> RADEON: No matching Device section for instance (BusID PCI:1:0:1)
This is the key line.  You might be able to sort out why it can't find a "Section Device" that matches that BusID, but you're probably better off to regenerate the default config file and start again with a file that works.

If a backup of the default was created for you when you edited it (which depends on what editor you used and what your settings are) then you can use the "mv" command in the terminal to change it's name and thereby overwrite the one that's butchered.

---

### Post by charles hp on 2007-04-25
thanks for all the help guys. Yeah I guess I should have backed up that file :P

Anyway, I just booted to the live CD and reinstalled linux. Not the most elegant solution I guess but since I had just installed it minutes before, nothing was lost.

---

