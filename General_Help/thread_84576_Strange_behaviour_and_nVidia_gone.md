---
title: "Strange behaviour and nVidia gone"
date: 2005-10-31
forum: General Help
---

### Post by tcaptain on 2005-10-31
I've gotten some strange behaviour on my laptop, which has a new install of Breezy.

As of yesterday afternoon, all was well, I had installed the nvidia-glx packages, all was running fine.  KDE, Gnome, blackbox, all were well.

I installed a few packages, but nothing kernel related, with the exception of the Nessus packages which I wanted to check out, (I'm not sure they deal with the kernel or anything, I'm still learning).

I have not compiled a kernel, I'm using the one from the install.

When I logged and shutdown, all seemed well.

Now this morning as I boot up, X won't work.  I have an error about the nvidia module is not responding to interrupts (I will have to jump a few hoops and get the error messages back again).

reinstalling nvidia-glx doesn't help.

By changing my xorg.conf back again (nv instead of nvidia, etc..) I can load in 2D mode....however Gnome won't let me log in!  Xsession errors...when I track it down, for SOME reason my .ICEAuthority file now belongs to root and has readonly flag for root on it.  In console, I erase it, now I can get back into Gnome normally.

Another thing I noticed and fixed, the /media/hda1 mount point went from being world readable to root read only.

I'm using REISERFS, I don't think the drive is corrupt of the HD failing, the laptop's a month old.

I've fixed all the little weirdness, but I'm still out of 3D acceleration and would LOVE to get it back again...what should I check?

---edit---

A friend who uses ubuntu pointed me to an archive thread where the .ICEAuthority problem was caused by running K3b, however, while I've installed K3b yesterday, I haven't run it...haven't gone beyond installing it in synaptic.

---end edit---

---edit #2---
Alright, its now lunch so I figured I'd get the nvidia error by changing my xorg.conf BACK to the old settings and now everything works!  Humm...call the X-Files.
---end edit---

---

