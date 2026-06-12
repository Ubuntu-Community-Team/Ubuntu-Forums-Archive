---
title: "No graphical login"
date: 2007-12-04
forum: General Help
---

### Post by jmcgee on 2007-12-04
I walked in one day, and my gnome desktop was gone and I was looking at a terminal.

On boot, I get the first graphic Ubuntu, then dropped to terminal, the first line is red FAIL (with no text before it), then more text, then login.  I login and get prompt,  Startx brings up the desktop.

From desktop I went to terminal and typed
 sudo dpkg-reconfigure gdm

and got

 * Reloading GNOME Display Manager configuration...
 * Changes will take effect when all current X sessions have ended.
invoke-rc.d: initscript gdm, action "reload" failed.

Any ideas how to solve thiis?

---

### Post by Sef on 2007-12-05
1) What are your system specs?

2) Do you have a spare graphics card?  If so, take out the current one, and put the other one in.   If it works, then you have a bad graphics card.

---

### Post by jmcgee on 2007-12-05
I noticed something else.  From GNOME desktop, System|Administration|Login window results in

GDM (The Gnome Display Manager) is not running
You might in fact be using a different display manager, such as KDM (KDE Display Manager) or xdm. If you still wish to use this feature, either start GDM yourself or ask your system administrator to start GDM.

weird, since isn't GDM displaying that message?

---

### Post by jmcgee on 2007-12-16
More on this from the xorg log:

(II) Module int10: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.1
(WW) NVIDIA(0): Unable to load "xf86ExecX86int10".
(EE) NVIDIA(0): Unable to initialize the X Int10 module; the console may not
(EE) NVIDIA(0):     be restored correctly on your TV.

This on 7.04 system.

On a hunch, I used Envy to reload Nvidia drivers, but no change.

---

### Post by jmcgee on 2008-01-14
Never mind I fixed it. thanks so much.

---

### Post by knutschr on 2008-01-14
> **jmcgee said:**
> Never mind I fixed it. thanks so much.
How did you fix it?

---

