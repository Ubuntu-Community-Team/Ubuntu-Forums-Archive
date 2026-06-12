---
title: "Ubuntu annoyance #5:  Workspace tweaks on reboot"
date: 2015-03-12
forum: General Help
---

### Post by DigiAngel on 2015-03-12
I use the great UbuntuTweak, which allows me to workspace screen edge actions (a quick flip of the mouse to the bottom corner and I have an Expose like view of all my windows).  This sometimes goes away on reboot.  It's set correctly when I go to UbuntuTweak, so I set it to something else, set it back, and things are fine.  Debugging showed nothing interesting...is there a way to get this to stick all the time?  Thanks.

---

### Post by CantankRus on 2015-03-12
Compiz is just plain flakey.
I have screen edges+mouse1 set up to do certain things and 
usually don't work after logout/in.
Quick fix is to reload compiz with the command **setsid unity** which I have set to a keyboard shortcut.

---

### Post by DigiAngel on 2015-03-12
Ah thanks...I'll give that a go.

---

