---
title: "Can I disable gnome-power-manager?"
date: 2007-05-03
forum: General Help
---

### Post by canadianwriterman on 2007-05-03
Ever since doing a fresh install of Feisty on my HP desktop, I've had a problem with the monitor shutting off if left unattended for a long period of time (like overnight). Changing the power management setting (even though I think they are only for a laptop) to "never" doesn't help.

Last night I disabled the running gnome-power-manager session and the monitor did not shut down overnight. Assuming that was my problem, can I safely permanently disable gnome-power-manager from starting on boot, or is it needed for a desktop as well as a laptop? 

This is a problem I never had with Dapper or Edgy... seems to have been introduced with Feisty. Thanks for your help.

[EDIT: The reason this is an issue is that the monitor cannot be restarted, except by shutting down the computer and restarting.]

---

### Post by pixelmonkey on 2007-05-04
You can disable gnome-power-manager by going to System->Preferences->Session, if memory serves.  The first panel lists programs which run at startup of your Gnome session.

Advanced stuff to follow up on issue:

You might also want to do research on "DPMS" settings, and in particular take a look at the command "xset q", which will list your DPMS settings.  Run gconf-editor and search for "gnome-power-manager."  You can find settings related to monitor sleep and how it uses DPMS there.

If your monitor doesn't resume from DPMS blanking, then I also recommend you file a bug at Launchpad to help the developers sort it out.

Andrew

---

### Post by canadianwriterman on 2007-05-06
Very helpful direction, pixelmonkey. I found a Feisty bug report related to screen blanking. Fits my situation, as I never had the problem before Feisty. One solution reported was to X-out the DPMS option in the xorg.conf file. So, I've done that and we'll see what happens. I have to leave the computer idle for several hours before the problem shows. I'll let you know what happens.

---

### Post by canadianwriterman on 2007-05-06
Sorry, double post.

---

### Post by canadianwriterman on 2007-05-06
X-ing out "DPMS" in the xorg.conf file did the trick. Thanks, pixelmoney!

---

### Post by Toadmund on 2007-05-06
Screen blanking?
Like in here:
[http://ubuntuforums.org/showthread.php?t=420888]("http://ubuntuforums.org/showthread.php?t=420888")

This problem is going to make me bald!

---

### Post by canadianwriterman on 2007-05-06
Not quite. My monitor shut right off. Turns out it was the Energy Star being implemented in my monitor. I changed the DPMS (Energy Star control) to disable by X-ing it out of xorg.conf.

---

