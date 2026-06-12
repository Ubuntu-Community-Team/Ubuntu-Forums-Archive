---
title: "Change keyboard layout"
date: 2008-03-20
forum: General Help
---

### Post by andradx on 2008-03-20
I'm having some trouble with Matlab. Whenever I try to use the power symbol ^, if I just shift+~ and then write (say 2) it automatically prompts 2 into upscript, which of course is of no use for upscript is not recognized as power.

So I've added to my Portuguese layout a Portuguese with dead keys layout and to swap between layouts a quick Alt+Alt Gr does it.

What I was trying to do now was automatize the mechanism, whenever Matlab was initialized the dead keys layout came into action, and on leave it would enable the standard Portuguese layout. However I don't know how to change layouts using a shell:confused: Can someone help me?

---

### Post by tnic on 2008-05-16
Have you found a solution? I have exactly the same problem, its frustrating not to be able to use the maple editor just because of this silly keyboard layout issue.

---

### Post by olejorgen on 2008-05-16
[http://ubuntuforums.org/showthread.php?t=597890](http://ubuntuforums.org/showthread.php?t=597890)
[http://ubuntuforums.org/showthread.php?t=554952](http://ubuntuforums.org/showthread.php?t=554952)

might help

Look into xmodmap too

Maybe 
xkeysw - A keyboard layout switch for the X Window System
xkeysw-config - xkeysw configurator
too

---

### Post by tnic on 2008-05-17
Thanks a lot! That solved my problem.

---

