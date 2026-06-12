---
title: "Deleted a few things in synaptic, now my resolution is too low"
date: 2014-07-15
forum: General Help
---

### Post by linux_dream on 2014-07-15
I've been "playing" with synaptic (wanted to install a newer kernel and remove my old ones). Problem is, seems like I've deleted some packages I shouldn't have, because after a reboot my resolution changed and I can't modify it back. Now in the menu, System Tools -> NVIDIA X server settings,  there are very few options compared to what it used to be!  I do still have the correct nvidia drivers installed (my graphics card is a geforce 7300 GS). So I don't know how to fix the problem. My guess is that I should reinstall a package I deleted, but I don't remember which ones I deleted. I've tried to google to check for a command to see the latest deleted packages but to no avail. Any help is appreciated!

---

### Post by linux_dream on 2014-07-15
Problem solved. Turns out that the nvidia drivers were not in use anymore and I had to blacklist the nouveau drivers: sudo gedit /etc/modprobe.d/nouveau.conf Then in that file add the following 2 lines:  blacklist nouveau options nouveau modeset=0 Then save and reboot :)

---

### Post by oldos2er on 2014-07-16
For future reference, in Synaptic go to File, History, to see which packages were installed or removed.

---

### Post by linux_dream on 2014-07-16
> **oldos2er said:**
> For future reference, in Synaptic go to File, History, to see which packages were installed or removed.  Thank you very much! I wasn't aware of this.

---

