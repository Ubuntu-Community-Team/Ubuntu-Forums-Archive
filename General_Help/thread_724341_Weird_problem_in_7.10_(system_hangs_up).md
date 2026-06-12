---
title: "Weird problem in 7.10 (system hangs up)"
date: 2008-03-14
forum: General Help
---

### Post by napolperro on 2008-03-14
Ok so this is my first post, I have been using Ubuntu a couple months now, installed it in both my desktop and laptop, dualbooting with xp.

Everything works fine on the desktop, but I'm having this problem in the laptop, whenever I try to drag something (an image from firefox, a background for the folders, an icon, etc) the whole system crashes, just like that, I can still move the mouse around, but cannot click on anything, the keyboard is unresponsive and the only way to use the computer again is holding the power button for several seconds until it reboots.

Also, when I close the lid of the computer and then open it again, the screen is blank, I can again move the mouse around but everything else is black, and the keyboard stops responding (ctrl-backspace and the like won't work)

My system is a Dell Inspiron 6400/E1505 with the onboard graphics and a Centrino Duo @ 1600 Mhz.

I found something in another forum that said the transparencies of the panels were bugged, since i had turned them on I thought that was the problem but I'm still having it.

Any help would be really appreciated.:confused:

---

### Post by napolperro on 2008-03-15
Anyone?  Please this situation is really annoying :(

---

### Post by prshah on 2008-03-15
> **napolperro said:**
> Anyone?  Please this situation is really annoying :(

When your system freezes up, try the Ctrl+Alt+SysReq+"E" (to terminate all running process and drop to a terminal) or "B" (for instant reboot).

(In a laptop, to get to the SysReq key you may have to also press the "Fn" key if you have something like that).

If neither of these work, you probably have a hardware problem, but in either case you might want to :

1) turn off power management for the hard drive (in the bios)
2) turn off screensavers
3) Are you using an external mouse that is conflicting with the inbuilt finger pad?
4) Have you installed both KDE desktop and Gnome desktop? I have found that installing both causes random lockups. Many others have found no problems though, this is MY personal experience, I have NEVER got both Ubuntu and Kubuntu to work and play together. If you want to check if you have both installed, use the command ```
ls /etc/init.d/?dm
``` if it lists both "gdm" and "kdm" then you have both installed.

---

### Post by napolperro on 2008-03-16
Thanks for your answer!

I have tried the key combinations, but it appears that the system just ignores the keyboard when it hangs up like this.

I am not using an external mouse, and I haven't installed KDE and Gnome, so the other options I have left are the screensavers and the HD, so I'll try them and hope it works.

---

