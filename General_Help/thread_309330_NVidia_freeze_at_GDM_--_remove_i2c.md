---
title: "NVidia freeze at GDM -- remove i2c?"
date: 2006-11-29
forum: General Help
---

### Post by lithium on 2006-11-29
I recently did a new Install of Edgy on my main computer and since then I am unable to run the NVidia binary driver. I don't want to use the driver from the .deb, so first thing I do is

sudo apt-get uninstall --purge nvidia-kernel-common nvidia-glx linux-restricted-modules-generic linux-restricted-modules-common

This is fine and all but after installing my own version of the NVidia driver (9629 or 9742) my computer freezes at the GDM prompt.  Using the "nv" driver works and changing the driver while running (gdm stop / replace driver in xorg.conf / gdm start) also works!

I have read that there are some issues with i2c and the newer NVidia drivers... is there a way to disable i2c totally?

---

### Post by lithium on 2006-11-29
Perhaps this is of note: when I boot into save mode and start GDM by hand it works fine!

Also, installing Ubuntu's 8776 driver works fine... but I cannot seem to get how to install that version by hand to compare... any idea?

---

### Post by lithium on 2006-11-29
Also: I have removed gdm now, so I boot into a terminal. From there I start the same X/Gnome session I would start using GDM and it works just fine! Now what may be wrong with booting into GDM? I'm thankful for any hint :/

---

