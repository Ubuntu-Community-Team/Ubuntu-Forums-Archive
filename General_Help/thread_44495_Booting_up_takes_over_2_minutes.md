---
title: "Booting up takes over 2 minutes"
date: 2005-06-26
forum: General Help
---

### Post by Tyr_7BE on 2005-06-26
99 seconds.  That's the amount of time my laptop sits idle, displaying "Starting Enterprise Volume Management Systems...", giving me plenty of time to watch the hard drive activity light stay constantly on.  That's all it does....it sits there with IDE light blazing, and a really faint sound coming from the hard drive, like it's reading/writing something.  I just timed it and it took a full 99 seconds to move on to the rest of the boot process.  Before and after this stage, it's just fine.

Now it wasn't always like this.  When I first installed Ubu, it was blazing fast.  But as time progressed it got worse and worse.  Now it's to the point where turning the laptop on is a big deterrant....not something you want in a portable device.

Does anyone know what's going on?  Why does "Starting Enterprise Volume Management System..." take so excruciatingly long?

Compaq Presario 2500, Ubu Hoary.

---

### Post by rockmusic88 on 2005-06-26
have you changed any of the dma settings?

---

### Post by Tyr_7BE on 2005-06-27
Nope.  It is using DMA, and always has been.

It also seems that everything is taking a really long time to access the hard drive.  Gnome startup takes forever (ie, over 40 seconds with the IDE light blazing, though I am running a LOT of software in my startup scripts).  Simply starting up epiphany takes so long that it starts to bug me.

Is file system fragmentation an issue on an ext3 filesystem?  I ran e2fsck on it from a live cd but it didn't help.

---

### Post by Tyr_7BE on 2005-07-04
No more ideas?  It's getting worse and it's becoming a real problem.  If it continues to get worse I'm reinstalling hoary to see if it fixes the problem.  Last time I had to do a reinstall to fix a problem was Windows ME.  It would be a shame to see my linux desktop falter as well.

---

