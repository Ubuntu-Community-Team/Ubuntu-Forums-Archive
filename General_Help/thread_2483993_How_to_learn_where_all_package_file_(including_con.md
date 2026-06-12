---
title: "How to learn where all package file (including configs) are stored"
date: 2023-02-14
forum: General Help
---

### Post by sofasurfer on 2023-02-14
I screwed up. I issued a mv command that moved all everything inside my /home directories to /Downloads. /Documents, /Pictures, /music, /Desktop, etc are all still there but they are empty. Their contents have been move to /Downloads. The files moved and the directories moved but the directory contents stayed in place. I can fix most of this. But my zim notebook program files are hard to locate. How can I determine ALL zim files and CONFIG files that I need to locate? Or basically, how do I save my zim work?

---

### Post by MAFoElffen on 2023-02-14
I may be wrong, but, as I understand the config file $XDG_CONFIG_HOME/zim/automount.conf is where those settings are or can be changed from...

---

### Post by sofasurfer on 2023-02-14
I saw that info in the zim wiki but so far I am not able to locate that file

---

### Post by MAFoElffen on 2023-02-14
I would search recursively through your home directory. But as you explained you move all $HOMEinto $HOME/Downloads... and  automount.conf was stored in ~/zim/, I would suspect that the zim directory is now at $HOME/Downloads/zim.... If you move at directory back to $HOME, everything for that should straighten back out. That would be my guess.

---

