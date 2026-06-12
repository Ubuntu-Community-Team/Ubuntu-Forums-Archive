---
title: "Problem with Painter IX under Wine"
date: 2007-05-26
forum: General Help
---

### Post by Malachi Wolfe on 2007-05-26
Hi, 

I'm fairly new to Ubuntu, I have feisty installed and I'm having some serious problem with trying to run Painter IX under Wine. 

The program seems to have installed fine, and will open fine. But as soon as it opens, Painter will freeze and stop responding. I've tried rebooting, and uninstalling and reinstalling, but the problem is still there.

Has anyone else run into this? Any suggestions?

---

### Post by MoLE on 2007-06-02
Have you tried running the application from a terminal?  What terminal output do you get when it crashes?
Which version of windows emulation are you running Painter on?  Try downgrading it using winecfg.

---

### Post by Malachi Wolfe on 2007-06-05
I've tried downgrading winecfg, in XP, ME and 2000, though I havent tried an earlier version of Painter yet.

This is the error it gives:

Xlib:  extension "XFree86-DRI" missing on display ":0.0".
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
fixme:win:WINNLSEnableIME hUnknown1 0x10024 bUnknown2 1: stub!
fixme:win:UpdateLayeredWindow (0x1002a,0x308,0x33e3d0,0x33e3d8,0x5cc,0x33e3e0,0x00000000,0x33e3cc,2): stub!
err:x11drv:X11DRV_CreateWindow invalid window width -16
fixme:wintab32:X11DRV_WTInfoA Return proper size
Xlib:  extension "XFree86-DRI" missing on display ":0.0".



....and this is where it freezes.

---

### Post by MoLE on 2007-06-05
From the error output, it seems that the problem is not with wine, but with your Xorg configuration.  Wine is complaining that it can't access the DRI extension via xlib for some reason.  DRI = direct rendering infrastructure, which is an extension which can be enabled in Xorg if your hardware and driver supports it?

Looks like we need more information:  Which video card does your computer have?  Can you post your xorg.conf file as an attachment here?

---

