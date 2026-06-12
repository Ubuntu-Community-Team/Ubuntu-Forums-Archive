---
title: "After Hardy Upgrade, Login stops at &quot;Running local boot scripts&quot;"
date: 2008-04-27
forum: General Help
---

### Post by tnk207 on 2008-04-27
Hello,
I'm running Kubuntu on a Toshiba Portege M400.  Upon upgrading to 8.04 via Synaptic yesterday, an interesting problem emerged.  Starting up, the computer makes it all the way to the login screen, but when I enter my information, the screen goes blank, then cuts to the command line, where the system seems stuck at the infamous:

"Running local boot scripts (/etc/rc.local)         [OK]"

If I press ENTER, nothing happens.  If I do CTRL-ALT-F1, I can get to the command line and do startx.  But then it boots into gnome, and not KDE, which is my default desktop environment.  If I try to login to a Gnome or Failsafe session this way, the same thing happens.

I've checked rc.local, it appears normal, my xorg.conf is fine, I've checked the TTY files, which, given what I've read (no idea what they do) seem okay.

I'm at a total loss for how to fix this.  The fact that I can get to the login screen, but it cuts out from there is an aspect of the issue I haven't seen anywhere else.

Any help would be greatly appreciated.

---

### Post by danwood76 on 2008-04-27
You must have some startup scripts which are causing issues with hardys KDE.
Are you able to login straight to a GNOME session from the login screen?

I dont know KDE so I cant really help with regards to clearing the startup scripts.

---

### Post by tnk207 on 2008-04-27
Can't login to gnome or failsafe from the login screen either.

---

