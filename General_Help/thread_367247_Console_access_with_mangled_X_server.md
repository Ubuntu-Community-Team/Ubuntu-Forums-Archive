---
title: "Console access with mangled X server?"
date: 2007-02-21
forum: General Help
---

### Post by Dave / Mosaic on 2007-02-21
Just getting used to Linux here, with Xubuntu 6.10 recently installed (PowerMac G3) after some long installation battles with getting stuck on aec62xx and such...

My question today is:  Suppose you screw up your X server, as I have done, by misguided experimenting with dpkg-reconfigure xserver-xorg, such that when you boot, X refuses to start, and all you get is a useless messed up screen with colors like from a bad trip...

Is there some way to interrupt or circumvent the normal boot sequence, such that you can get a plain console terminal, instead of the normal path to a window manager via X?

I'd sure like to know...

---

### Post by taurus on 2007-02-21
Just boot into recovery mode that you can run that command again to reconfigure X.

```
dpkg-reconfigure xserver-xorg
```

---

### Post by Dave / Mosaic on 2007-02-21
Okay,,,  sorry to be dumb, but how do I do that?

(Thanks for the fast reply,,,)

---

### Post by boredandblogging.com on 2007-02-22
When you boot, and grub does that countdown, press escape and you will be shown the list of available kernels. Pick your "-recover" or something similar kernel and continue booting.

---

### Post by Dave / Mosaic on 2007-02-22
Okay, thanks for the reply...  however:

My installation is on a PowerMac G3, so I'm thinking things may be a bit different here; I can't see how to do what you suggesting to try - nothing that I would call a "countdown" occurs during booting.

Here is what I see happening during my boot sequence:

yaboot (bootloader on the mac - corresponding to GRUB on the PC??) runs, and gives a choice of booting linux from hard disk, or else from whatever CD it finds...

some other program (my understanding of the boot sequence is pretty limited) then loads and runs, with a prompt that says "boot:" and suggests that you can type help...

when I type help, it says you can press tab for a list of available kernels...

so when I press tab, it lists two choices - "Linux", and "Old" (no idea what that is)...

once I tell it to choose Linux, then it just loads the kernel and starts X, without any further options...

Is there something that I'm missing here?

Sorry to keep bugging the list about this, but I'm not sure where to look in any documentation to find the answer myself...

Thanks again--

--dave

---

