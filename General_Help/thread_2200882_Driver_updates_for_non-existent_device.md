---
title: "Driver updates for non-existent device"
date: 2014-01-21
forum: General Help
---

### Post by Silvernail on 2014-01-21
I just got driver update for HP printer. I DO NOT own a HP printer. I have a Samsung.
This is not the first time I received updates stuff I don't have. Why do I get these?

If I don't install them, they won't go away. How do I erase them from the list?

---

### Post by The Cog on 2014-01-21
You could find them in synaptic and remove them if you really want. There are probably only a few thousand. But why worry? Doing that won't save a lot of disk space, and drivers won't get loaded unless there's something that needs driving.

---

### Post by ajgreeny on 2014-01-21
Have you considered how many modules may be already installed with the kernel that you never use; they are just part of the overall build but are not loaded unless needed by hardware.  There are also many different xserver-xorg-video-*** packages installed by default in Ubuntu but you will only normally be using one of those at any time, ie the one appropriate for your hardware.

---

### Post by grahammechanical on 2014-01-21
If things were not done this way we would need a version of Ubuntu for those with HP printers and a version for those with Samsung printers. Or we would all get a version without any printer drivers and would have to install the driver that is provide by the printer manufacturer. But manufacturers do not provide Linux drivers for their hardware.

---

