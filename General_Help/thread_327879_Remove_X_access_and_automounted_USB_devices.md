---
title: "Remove X access and automounted USB devices"
date: 2006-12-29
forum: General Help
---

### Post by mpthompson on 2006-12-29
Hello,

I'm using an Ubuntu based PC for software/hardware development in conjunction with a Windows XP system.  To make my life a little easier for development on both platforms I have enabled System->Administration->Login Window->Remote and enabled XDMCP to support remote X server access.  I then installed the Xming X server on my Windows XP system and I have both the Windows XP and Ubuntu desktops relatively well integrated as a unified environment.

The issue I have is that GDM/Gnome/X11 seems to treat my remote XDMCP X session different from an X session on the local console of the Ubuntu system.  My first problem is that USB devices plugged into a USB port are not automatically mounted with an icon on the Gnome desktop when I'm logged in over an XDMCP X session.  However, automount does work as expected when my X session is on the sytem console.  The other issue is that in the GDM login greeter and when I'm logging out of the XDMCP session I'm not given the usual "suspend, hibernate, restart, shutdown" options. 

My assumption is that GDM/Gnome/X11 by default is configured to assume that an XDMCP session is from a remote location away from the system hardware.  Thus it disables certain actions that would make sense in such a configuration.  However, I'm wondering if there are some magic settings in Gnome so that automount will work for an XDMCP X session just as it does on a local console X session.  Does anyone have ideas on where I can look?

Hopefully my description above makes sense.  Thank you for any help someone can give me.

Mike Thompson

---

### Post by mpthompson on 2006-12-30
I've investigated this a bit further and it appears that the gnome-volume-manager doesn't start for XDMCP X sessions.  I've tried to start it manually, but it just exits immediately with no warnings or errors that I can find.  Any ideas?

Mike

---

