---
title: "SOLVED: Today's Update Broke Lightdm - Revert to old version necessary"
date: 2013-05-17
forum: General Help
---

### Post by roots on 2013-05-17
Hi,

I'm running Ubuntu 12.04 with gnome classic. Todays update somehow broke my X / Gnome Classic: When booting, I'm not getting my greeter to log in but a command line login prompt. After logging in this way, I can do startx and get my desktop with Compiz running - but without Gnome Panels etc.

Any suggestions on what to do are VERY MUCH appreciated!!!



Thanks.
roots

---

### Post by roots on 2013-05-17
I just figured out that I can successfully launch Gnome Panel by hand, but still: How do I get the whole thing to start up automatically again btw. where to look for why it doesnt?! Plus: On manual startx I now do get a keyring password prompt that I did not get normally. Any suggestions?!


Thanks.
roots

---

### Post by grahammechanical on 2013-05-17
So, to be clear you are not able to go from the Grub boot menu to a Ubuntu login screen without getting a command line prompt where you type startx.

Try, at the Grub menu select Ubuntu Recovery mode. At the Recovery mode screen select Resume. That may get you to the log in screen and a desktop where you can use Additional Drivers to activate a video driver. That may be the problem. Especially if the update brought in a kernel update.

Regards.

---

### Post by roots on 2013-05-17
Thanks graham for the quick reply.

Selecting recovery mode with the updated kernel and chosing resume does get me to the same cmd login prompt.
The same happens if I pick an older kernel version, no matter if regular or recovery mode.
If, in recovery mode, I select failsafeX, I'm getting "Fatal Error - no screen found".

I've been using the same ATI Catalyst driver 12.3 without any issues for about ... a year or more (since it was released).
Still, when manually starting X and Gnome Panel, everything works like a charm, this is what confuses me.

I'm a bit clueless at the moment, so still: Any help appreciated!


Thanks.
roots

---

### Post by garyzw on 2013-05-17
I am using nvidia drivers and after todays up date the screen resolution in the boot grub menu and the 1024 x 768 resolution of Urban Terror no longer goes to wide screen.

---

### Post by roots on 2013-05-19
Alright, here goes:

After some research into what might have broken my X, it turned out that it is actually lightdm that is "broken" - or breaks my X.
The last update brought the following to packages:

lightdm_1.2.3-0ubuntu**2.1**_amd64.deb
liblightdm-gobject-1-0_1.2.3-0ubuntu**2.1**_amd64.deb

They do break my X in so far that neither of the installed greeters (lightdm-gtk-greeter, unity-greeter) will start up and I'm left with the command line prompt.

**Solution:**

remove both packages (both greeters are removed as well, so you'll have to reinstall them later), get the previous package versions from the web as .deb:

lightdm_1.2.3-0ubuntu**2**_amd64.deb
liblightdm-gobject-1-0_1.2.3-0ubuntu**2**_amd64.deb

and install them manually. Reinstall the greeter(s), reboot and - enjoy a working system again.


Good luck,
roots

---

### Post by JiriG on 2013-06-14
I had the exact same problem, running Gnome Classic on an Ivy Bridge HD4000. I could restart X and lightdm from the command prompt by doing:

sudo service lightdm restart

This brought up X and lightdm and I could login as usual. Maybe switching gdm would be a better option ...?

Jiri.

---

