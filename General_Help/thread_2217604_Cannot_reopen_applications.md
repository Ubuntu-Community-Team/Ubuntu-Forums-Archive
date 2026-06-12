---
title: "Cannot reopen applications"
date: 2014-04-18
forum: General Help
---

### Post by fisch246 on 2014-04-18
So I upgraded to 14.04 no problems at all. Works great. I say this to make it clear this isn't a bug, it's apparently a feature. I would like to figure out how to turn it off. The feature being that you can open multiple sessions of an app with the middle mouse button. This feature has issues in that it doesn't know when an app is finished running. So after I open an app once, I can't open it again, ever, during the entire session, unless I use the middle mouse button. Or I log out. I'd say everything added to this release has been utterly fantastic except for this. One more side note, I don't have options in my titlebar. As in file and what not when a window isn't maximized, wasn't that supposed to be a feature this release, or was it dropped? To be more clear, it still only appears at the top, and not on the window. Thanks for any help provided.

---

### Post by fisch246 on 2014-04-18
Oh figured out the titlebar thing. Though the launcher problem is still an issue.

---

### Post by 3rdalbum on 2014-04-18
> **fisch246 said:**
> I say this to make it clear this isn't a bug, it's apparently a feature. I would like to figure out how to turn it off. The feature being that you can open multiple sessions of an app with the middle mouse button. This feature has issues in that it doesn't know when an app is finished running.

The feature is that you can open multiple sessions of a program with the middle-click button. Not knowing when a program has ended sounds like a bug, it doesn't happen on my computer. On my computer, if I close a program and then left-click on the Launcher icon, it opens that program.

Does this happen with every program? If this is happening with only one or two programs, it's possible that the program hasn't actually ended. You can find out with System Monitor. If the program is still running even after you tried to close it, then the program may be buggy and you should report the problem to its developers. For the meanwhile you can kill the program in System Monitor by right-clicking on it in the System Monitor list and choosing "End Process".

If the program is definitely not still running, then it must be a bug in Unity and you'll need to report it on Launchpad.

Disabling the middle-click will not solve your problem. It will just leave you completely unable to open a new instance of a program. Besides, I don't believe you can actually disable it.

---

