---
title: "Removal of a module at boot time question?"
date: 2007-02-05
forum: General Help
---

### Post by Turric on 2007-02-05
New to Ubuntu, so far it's great.

1 issue however.

Running 6.10, wouldn't recognize my USB flash drive.

Temporary fix was to remove the ehci_hcd module and it would recognize it.  However I have to use the sudo modprobe -r ehci_hcd command in the terminal each time to make it work after I've rebooted the comp.


Question: How do I keep this module from loading at boot time?  Is there a supported fix to this, with perhaps the graphical editor?

I'm not real linux savvy but I have a helper who is, although he's more familiar with Gentoo and helping over the phone, so we have some stumbling blocks.  If you could, walk me through like I'm a 3 year old.

---

### Post by Turric on 2007-02-05
No one knows?

---

### Post by cmost on 2007-02-05
I have an easy way to stop modules from loading: rename the rogue module to something else.  For example, go into wherever the ehci_hcd.ko module resides and rename it to something like ehci_hcd.ko.BAD.  To find the module, simply run a search throughout your filesystem.  When you find it, change to root to rename it.  Reboot.  The module will try to load and fail because it's 'not found' any longer.  Solved.  Be advised that this won't survive a kernel upgrade.  If you're like most of us, however, that won't be a problem.  Good luck.

---

