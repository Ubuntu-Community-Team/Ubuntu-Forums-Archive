---
title: "Disabling GDM disables power options?"
date: 2007-10-02
forum: General Help
---

### Post by Erdaron on 2007-10-02
Since GDM's login screen was broken for me, I decided to get rid of it. First, I tried to remove GDM using Synaptic, but it wanted to remove ubuntu-desktop as well, and I didn't want to go there.

So I renamed its link in /etc/rc2.d (from S17gdm to K83gdm, per instructions in the folder's README). Now on bootup I indeed end up with a text mode login screen, which is what I wanted. After logging in, I type startx and I'm back in Gnome.

However, then something odd happens. The shutdown applet in the top bar, then one that has buttons for shutting down, logging out, etc., no longer has options for shutting down or restarting. It can only suspend or hibernate (which don't work, probably because of fglrx drivers).

I can shut down from CLI using 'sudo shutdown -h now' but I don't want to do that every time. Is there a way to signal shutting down without having to use sudo?

Cheers!

---

### Post by zvacet on 2007-10-03
You can safely remove ubuntu-desktop.it is metapackage and no harm will be done by removing it.So,put things where they were before,and uninstall GDM.

---

### Post by Erdaron on 2007-10-04
Alright, I did that. Restored GDM in /etc/rc2.d then removed it (along with ubuntu-desktop) using Synaptic. Still the same problem - power off and reboot options aren't there.

Any suggestions?

---

