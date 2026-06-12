---
title: "AHCI (ICH9(R))/&quot;waiting for root files system&quot;"
date: 2008-06-13
forum: General Help
---

### Post by reesje on 2008-06-13
Hi guys,

I have a question that I hope you will be able to help me with.

Anyway, I enabled AHCI on my rig and booted Ubuntu (8.04). I actually works OK, but during boot I hangs some seconds a "waiting for root file system" (or something like that). During that period it searches the DVD ROM drive a few times.

Since I installed it without AHCI enabled, I thought that reinstalling Ubuntu might fix this problem. I had a spare disk so I installed a new copy on that.

It now turns out that the PC is unable to boot off the live CD. By using the parameter "pci=nomsi" makes it boot alright. But after installation was completed I had the exact same problem.

My question now is, am I missing the "pci=nomsi" anywhere on my installed system?

Thanks in advance.
Br, René

---

### Post by Rocket2DMn on 2008-06-13
Have you tried adding "pci=nomsi" to the kernel boot options in GRUB?  At the GRUB screen click "e" to edit a kernel, go to the "kernel" line and hit "e" again, add the option, then click enter to continue and "b" to boot.  If this works as you want it, you can add the options to /boot/grub/menu.lst
```
gksudo gedit /boot/grub/menu.lst
```
I think you add the option to the "# kopt" line or the "# defoptions" line to make the change permanent (even when update-grub is run).

---

