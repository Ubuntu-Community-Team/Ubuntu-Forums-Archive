---
title: "sudo apt-get autoremove PROBLEM"
date: 2007-11-06
forum: General Help
---

### Post by foxmulder881 on 2007-11-06
After performing a sudo apt-get autoremove command, it seems to have removed quite a few important files for some odd reason. Even my dictionary for OpenOffice.org seems to have been removed.

Is there a command to undo/reverse the last apt-get autoremove command?

---

### Post by mpierce on 2007-11-06
I've not found a way to restore after you do autoclean. 

As a result, I always backup my repos as it will remove things that are not in the standard repos such as skype, limewire, some libs that you download from other sources.

---

### Post by foxmulder881 on 2007-11-07
I can't understand why apt-get removed these files in the first place.

At least I grabbed a screenshot first so I know which files to reinstall...

---

