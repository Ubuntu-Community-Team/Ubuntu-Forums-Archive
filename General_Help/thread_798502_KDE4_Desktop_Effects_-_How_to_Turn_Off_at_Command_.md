---
title: "KDE4 Desktop Effects - How to Turn Off at Command Prompt? Screen BLACK!"
date: 2008-05-18
forum: General Help
---

### Post by OzzyFrank on 2008-05-18
OK, I installed Kubuntu KDE4 8.04 in Virtualbox, since I wanted to have a working Kubuntu (especially now I have to use it while figuring out what killed Gnome and Xfce!). KDE4 looked OK till I found the desktop effects and enabled a couple, and then the screen went black. At fist a couple of the open dialog boxes or whatever were there as white boxes, but now all I get is a black screen. When I log into Failsafe I have to use the terminal, so wonder what can I do with it to rectify this situation? Is there a command to kill the desktop effects?

---

### Post by meanerelk on 2008-05-18
You may find this thread of use:

[http://ubuntuforums.org/showthread.php?t=418138](http://ubuntuforums.org/showthread.php?t=418138)

---

### Post by OzzyFrank on 2008-05-19
Hi. That's actually for Gnome, and the "desktop effects" I am talking about are those that (I assume) come with KDE4, not (I assume) Compiz-Fusion (which I never enabled).

Still, might try some of that for the Gnome problem I am having (can't get past the splash after GDM login - which is why I am using KDE at the moment).

---

### Post by NightwishFan on 2008-05-19
Run this command:
```
mv /home/YOURUSER/.kde4 /home/YOURUSER/.kde4backup
```

---

### Post by OzzyFrank on 2008-05-20
Yeah, was saving that for a last resort, but did it and it worked. Always worried I'll lose too many settings, but in this case it didn't really matter, being that I'm running that Kubuntu KDE4 in Virtualbox anyway. Now if only doing the same in Gnome would fix things (I've renamed the .gnome2 folder and all, but still can't get it to boot past the splash going in to the desktop... though usually this tactic works and gives me my Gnome back, minus a few settings).

---

