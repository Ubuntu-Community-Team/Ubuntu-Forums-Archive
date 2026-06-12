---
title: "Nvidia driver xserver?"
date: 2007-11-30
forum: General Help
---

### Post by LokeTheDog on 2007-11-30
I just got a new computer, and was hoping to just put my old HDDs in it and get back where I left off basically.

Among other changes, I went from an old ATI-card to a Nvidia 8800 GT. So as expected, I had to download Nvidia drivers, which I did. The driver complained that x-server was running, and I don't know what that is, but I figured it would work if I rebooted in safemode, and it did. But when the install was completed and I rebooted again, the desktop manager wouldn't start. 

It said X-server didn't start because it was misconfigured (or something). In the next box it said "/etc/gdm/failsafeXServer line 47: too many arguments". Under that it said "Warning: Failsafe mode was already attempted in 30 seconds. Falling back to GDM to report the issue."

Then it said "X-server is now deactivated, restart GDM when it has been reconfigured"

Right now I just wanna get back into gnome, getting the driver to work is secondary. Thanks. :(

---

### Post by Juffo-Wup on 2007-11-30
Well, while you are in front of the console black screen, you could type (after logging in) the following command:

```
sudo dpkg-reconfigure xserver-xorg
```

and answer the questions that the 'wizard' asks.

---

### Post by LokeTheDog on 2007-12-01
Well, I tried that before and it didn't help...

But this morning, it started up just fine again. Very strange. I'll come back if the problem comes back. Thanks anyway.

---

