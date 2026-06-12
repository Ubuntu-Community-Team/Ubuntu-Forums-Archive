---
title: "How to safely remove/eject (not just unmount) USB hard drive from desktop?"
date: 2007-10-04
forum: General Help
---

### Post by Cupcake123 on 2007-10-04
Hi,

Is there any way to "eject" USB hard drives from the desktop GUI? I'm using Ubuntu 7.04, but info on whether this is possible with Kubuntu & Xubuntu would be good too.

There doesn't seem to be a way from the desktop GUI to "eject" my USB hard drive. I can do "eject /dev/sdc" or similar from the command line, but there doesn't seem to be a GUI equivalent for that. There is an option to unmount by right-clicking the desktop icon, but not to eject.

Note that this is distinct from unmounting partitions on the drive. Doing "eject /dev/sdc" (after unmounting all partitions of course) causes the drive to park its heads and spin down. That's very important prior to unplugging or switching off the drive. If the drive is simply turned off (or unplugged for USB bus-powered drives) while spinning, the heads are parked in a way which causes more wear and tear than spinning down the drive while it remains powered on. Over time, that could reduce the drive's life.

---

### Post by rsambuca on 2007-10-04
You could create a custom launcher and stick it on your top panel or desktop.

---

### Post by Cupcake123 on 2007-10-07
> **rsambuca said:**
> You could create a custom launcher and stick it on your top panel or desktop.

Thanks. Could you give some hint on how to do that?

Ideally I'd want it to work for any /dev/sdX device, since the device letter may change. The gnome-mount command might be the one to use???

---

### Post by rsambuca on 2007-10-07
I don't know how you would do it for sd*x*, but if you want to create a custom launcher, just right-click on the desktop and select "Create Launcher".  Then give it a name, type in your command, and give it a comment if you wish.  Icon is optional as well.  You can then leave it on the desktop for double-click action, or move it to a panel for single click action.

---

