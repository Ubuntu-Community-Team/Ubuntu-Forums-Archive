---
title: "gedit hangs when opening files in Ubuntu 14.04"
date: 2014-06-05
forum: General Help
---

### Post by rybu on 2014-06-05
Greetings, 

I'm having some trouble with gedit in Ubuntu 14.04.  I frequently use it when editing C++ source files.  Recently it has been hanging when opening source files via the "open" dialogue box.  It has no trouble opening files when requested from the command-line, but the dialogue box GUI "open file" function causes gedit to use all the CPU cycles from one core, and the window freezes.  

Is this a known problem, perhaps bigger than just gedit?   

I'd fill out something on Launchpad but I have so little data.   The program does not crash, it just uses one core fully. And the window becomes unresponsive (grays-out if you try to use it).

---

### Post by courtney2 on 2014-06-05
Same problem here on both my machines (running Ubuntu GNOME)

---

### Post by manrox-drag on 2015-01-27
i do have the same problem when searching for text in the file .gedit  hangs

---

### Post by coldraven on 2015-01-27
This may be nothing to do with your particular problem but is worth looking into.
Up until recently I was running 12.04 and my HDD started to go read-only on me. There were no error messages, my system just began to freeze etc. I checked the SMART data in the "Disks" utility and it said there were some bad sectors. The "Fix errors" option on boot-up did not help.
I did a clean install of 14.04 and bingo, no more errors and I get a faster boot-up.
Possibly one of the bad sectors was in an important place on the disc and a fresh install has avoided it.
My neighbours laptop running 14.04 has started to misbehave. The SMART data showed massive seek errors. (1500000) so I told him to buy a new drive.
In both cases the SMART data showed that the HDDs had been powered on for just over one year. We are both getting SSDs!
In any case I recommend doing a fresh install of 14.04, it's a great improvement over 12.04.

---

