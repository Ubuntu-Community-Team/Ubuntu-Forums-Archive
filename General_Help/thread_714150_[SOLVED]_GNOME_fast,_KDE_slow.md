---
title: "[SOLVED] GNOME fast, KDE slow"
date: 2008-03-03
forum: General Help
---

### Post by fiftyMIPsparc on 2008-03-03
Hi all, I'm running Gutsy on an IBM T43 (Centrino 2 GHz w/ a gig of ram). This was an Ubuntu install but I decided I wanted to install KDE also. Once installed, KDE seems to run very slowly. It takes forever to redraw screen elements and the UI is sluggish overall. GNOME has no problems at all and seems much more responsive. I know this isn't the nature of KDE, so I think something must me misconfigured... however, i don't think its a graphics acceleration problem, because I can load up Google Earth and spin the globe around without a problem, just as fast as in GNOME.

Anyone have any suggestions? Thank you very much in advance.

---

### Post by kellemes on 2008-03-03
What videocard do you have? And what driver have you installed for it?
I remember having this in the past when I used KDE with XGL.

---

### Post by fiftyMIPsparc on 2008-03-04
It's a Radeon Mobility X300. Yes, I'm using XGL. Is there any way I can keep my graphics acceleration and continue to use KDE and GNOME?

---

### Post by sstusick on 2008-03-04
It might help to change the KDE theme, I switched to Plastic and it is much more responsive. I uninstalled Dolphin and used Konqueror for a file manager and that helped as well.

---

### Post by kellemes on 2008-03-04
> **fiftyMIPsparc said:**
> It's a Radeon Mobility X300. Yes, I'm using XGL. Is there any way I can keep my graphics acceleration and continue to use KDE and GNOME?

And you're using the fglrx-driver? And what version?
I think from version 8.42.3 and up fglrx makes use of AIGLX, which means you can disable XGL as long as you have the following section in /etc/X11/xorg.conf
```

Section "ServerFlags"
        Option  "AIGLX" "true"
EndSection

```

You need to remove the xgl package like so..
```
sudo apt-get remove xserver-xgl
```

Important: Remember what you did so you can always revert. ;-)

---

### Post by fiftyMIPsparc on 2008-03-05
I had fglrx 8.455.2-0ubuntu1. I added those lines to my xorg.conf and removed XGL, and it looks like i'm back to Metacity in GNOME. KDE is blazing fast, though. I still have 3D acceleration, which is good... but is it possible to still keep compiz effects in GNOME? Or am I trying to get the best of both worlds?

---

### Post by kellemes on 2008-03-05
> **fiftyMIPsparc said:**
> I had fglrx 8.455.2-0ubuntu1. I added those lines to my xorg.conf and removed XGL, and it looks like i'm back to Metacity in GNOME. KDE is blazing fast, though. I still have 3D acceleration, which is good... but is it possible to still keep compiz effects in GNOME? Or am I trying to get the best of both worlds?

3d-stuff is now provided by AIGLX instead of XGL, so that should work fine..
Can't hurt to try though.. just choose Gnome with the session-button in your login-screen and see if it works.

---

