---
title: "configure video drivers"
date: 2008-05-02
forum: General Help
---

### Post by aalr1986 on 2008-05-02
hey....
I just downloaded Ubuntu Hardy Heron, and I don't know how to configure, or change my video drivers. I have a laptop DELL Vostro 1500, and an NVidia GeForceFX 8600M GT 256mb, and the biggest resolution I get is 800x600.

How do I change, or configure this, or how do I change the drivers?!??!

---

### Post by jaredbuck on 2008-05-02
The process for getting your 3D drivers working depends on whether you use GNOME or KDE. In GNOME it's very easy to get it working - in the System menu under Administration (or Preferences, I can't remember which right now) there should be an option for your restricted video drivers. Checking the box next to your card should get the system to download the appropriate driver for your card.

If you're using KDE you'll have to use a package manager to download the drivers. You would be looking for the package called "nvidia-glx" I believe.  There are three different versions of this package - each is designed for a different set of Nvidia cards. 

From the command line you can 'sudo apt-get install nvidia-glx'. Make sure you read the package description to get the right one for your card.

Jared

---

### Post by aalr1986 on 2008-05-02
I'm using GNOME, and I actually tried that, and it downloads the driver, but still the same problem....
so like, when I enable the box, desktop effects work, and everything works fine, BUT the resolution.....

any other suggestion?!?!?

---

### Post by h218design on 2008-05-03
have you tried System > Preferences > Screen Resolution?

---

