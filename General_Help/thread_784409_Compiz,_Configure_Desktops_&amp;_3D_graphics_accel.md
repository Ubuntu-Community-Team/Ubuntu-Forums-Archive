---
title: "Compiz, Configure Desktops &amp; 3D graphics accelerator"
date: 2008-05-06
forum: General Help
---

### Post by p1r8bunn3 on 2008-05-06
Hi all,

Wow.  I've been reading this forum for about year and this actually the first time I've really needed to post.  Usually all my questions are already answered.  I did do a search for this and I came up empty.  I do apologize ahead of time if I missed something.

Anyway, let me start with a run down of my computer and then I'll ask from there.

AMD 64 bit processor
ATI Radeon x1200 integrated
Kubuntu Hardy Heron 8.01

I installed the compiz "advanced desktop effects setting" gui thing before realizing that while the graphics card was installed the 3D accelerator was not.  I installed the accelerator and now I can't adjust how many desktops I have.  I don't know if it's a setting I missed or it was the order I did things.  So, now the desktop flips like a board with two sides.

Any ideas?

Thanks for your help.

---

### Post by GOROSSI on 2008-05-06
If get what you are saying, you trying the KDE desktop settings as I had that problem as compiz Bypasses it resulting in just two desktops

You will need to set the desktops under "desktop Cube" in the  compiz advanced setting manager , four is the minimum for the cube after a reboot all four desktop buttons should on the panel

hope that helps.

---

### Post by p1r8bunn3 on 2008-05-07
> **GOROSSI said:**
> If get what you are saying, you trying the KDE desktop settings as I had that problem as compiz Bypasses it resulting in just two desktops

You will need to set the desktops under "desktop Cube" in the  compiz advanced setting manager , four is the minimum for the cube after a reboot all four desktop buttons should on the panel

hope that helps.

Thanks for your help.  It seems somehow I screwed things up beyond repair so I did a clean install and this time I installed the 3D accelerator right away. I installed the advanced settings manager thing along with compiz dpkg and I added emerald because that seemed to be missing from the "how-to's" I came across.  Now I'm getting the following error and I don't understand it:

root@Bunnyware:/home/bunnygirl# compiz --replace
Checking for Xgl: No protocol specified
xvinfo:  Unable to open display :0.0
not present.
No protocol specified
xset:  unable to open display ":0.0"
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log
Detected PCI ID for VGA:        Flags: bus master, VGA palette snoop, 66MHz, medium devsel, latency 64
01:05.0 0300: 1002:791e (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: not present.
Trying again with indirect rendering:
Checking for texture_from_pixmap: not present.
aborting and using fallback: /usr/bin/kwin
No protocol specified
kwin: cannot connect to X server :0.0

Please help.

Thank you in advance,
p1r8bunn3

---

