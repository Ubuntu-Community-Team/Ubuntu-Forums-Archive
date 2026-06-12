---
title: "X Server failure in VMware over Remote Desktop"
date: 2007-01-17
forum: General Help
---

### Post by misfit815 on 2007-01-17
I'm obviously pursuing this on the VMware forums, but I thought I'd post it here in case anyone has any helpful advice.  Note that I'm a Windows veteran who's been playing with Ubuntu in particular for several months now.

VMware: Workstation v5.5.3 build-34685
Host OS: Windows 2000 Server, SP4
Guest OS: Ubuntu Linux (Edgy Eft)

When connected to Windows via Remote Desktop (aka Terminal Services), guest OS is started and during boot process receives the following error:

"Failed to start the X server (your graphical interface).  It is likely that it is not set up correctly.  Would you like to view the X server output to diagnose the problem?"

The output is beyond me, and I get no further response from the guest.  This occurs during text-mode boot, and I never see GUI-mode boot (for obvious reasons).

Other notes: The guest boots fine locally (naturally).  Another guest (Windows 2000 Professional) has no problem booting via Remote Desktop.

Anyone got a clue what to do next?  Thanks for your help.

J

---

### Post by misfit815 on 2007-01-18
Ok, after some fiddling with xorg.conf and some other attempts, it finally dawned on me that I really don't need the X system up when connecting in this manner.

So then I looked for a way to keep it from loading by default.  I found a lot of information, but nothing seems to get me there.

I've tried modifying the grub menu.lst, but can't seem to figure out the right combination for loading multi-user, network-enabled, but not graphical.

I've tried shutting it off elsewhere, but the one common recommendation (modifying inittab) doesn't work for Ubuntu because the file doesn't exist.

So how do I keep X from loading?  Your help is appreciated.

J

---

