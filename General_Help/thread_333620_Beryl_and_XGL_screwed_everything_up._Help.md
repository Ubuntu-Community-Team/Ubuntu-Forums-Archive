---
title: "Beryl and XGL screwed everything up. Help?"
date: 2007-01-07
forum: General Help
---

### Post by stooge4ever on 2007-01-07
This afternoon I found a site that described how to install XGL and Beryl on Ubuntu. After I installed, I rebooted like the tutorial said, and now GNOME is not starting up. Since then, I've been going into the command line/terminal and following OTHER tutorials that show how to uninstall XGL and Beryl, and how to reinstall GNOME (I thought each one could've been the problem). Invariably, whenever I turn on my comp, the final screen that shows before it stops is the Ubuntu logo, the bar beneath it showing how far its loaded (almost full), and a thin, dashed blue line that crosses the top of said bar.
Help? Linux n00b here, so help would be greatly appreciated!
-AE
PS: ATI X1300 for a video card, if that makes a difference

---

### Post by Rich78 on 2007-01-07
You have to be very careful what you do after you have the first problem, not to do more damage by trying different things.

It may be more screwed now but try:

In grub choose Ubuntu version (recovery mode).

Let it boot to the console and type:

sudo apt-get remove beryl emerald-themes

Hopefully this should fix the problem, although you may well get an XServer error.

If so I can look up how to fix that or you could try reinstalling beryl by going back to the recovery mode and in the console typing:

sudo apt-get install beryl emerald-themes

Hope this helps

---

### Post by stooge4ever on 2007-01-07
Nope, didn't work.
Beryl was already removed, so I reinstalled it. 
Now I'm stuck on the same screen.
The "Blue-Lined Screen of Death".
-AE

---

### Post by nikdc5 on 2007-01-08
you've probably messed up your xorg.conf or gdm.conf - try replacing your current ones with any back ups you have in the folder.

---

