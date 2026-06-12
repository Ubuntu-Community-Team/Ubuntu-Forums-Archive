---
title: "Delay startup so external hard drives can mount"
date: 2008-04-26
forum: General Help
---

### Post by sddfdds on 2008-04-26
I have 3 external usb hard drives.  They do some sort of initialization during the startup progress bar, but if they dont do it fast enough, they aren't recognized once the desktop environment starts up, and I have to turn the ones that weren't recognized on and off to get them mounted.  Is there some way to delay startup for a few seconds so that they are all mounted when  the desktop comes up?

Thanks for any help

---

### Post by wdaniels on 2008-04-26
External drives don't really have to do much in the way of initialisation, and if gnome automounts the drives fine after booting, perhaps the problem is even the reverse of what you suggest. But in any case, it ought not to matter. Sure, there are ways to delay the boot process, but if this is any solution at all, it's not a good one, and I don't recommend trying that.

What would ultimately be better for both yourself and other users is to figure out why your drives don't always get mounted. To do that, you need to capture some log information. The next time you boot and the drives don't get mounted, run the following commands:

```
lshal > lshal.txt
dmesg > dmesg.txt
ls -l /dev/sd* > devices.txt
```

It would be best to open a bug for the issue in launchpad and post the 3 files created (lshal.txt, dmesg.txt and devices.txt) there with the bug report.

I can see already some similar bugs in launchpad (e.g. bug #110555) but there doesn't seem, at least from a cursory glance, to be anything very general or conclusive to explain the problem so far.

---

### Post by sddfdds on 2008-05-01
I was experiencing this on Gutsy.  After a couple restarts with Hardy, the drives have all been mounted, so this might be solved.

---

