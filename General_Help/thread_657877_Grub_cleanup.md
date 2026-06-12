---
title: "Grub cleanup"
date: 2008-01-04
forum: General Help
---

### Post by trickypig on 2008-01-04
I've been running Ubuntu for a while now, so whenever I boot, grub gives me dozens of options.  There are 2 options for every version of the kernel.  I dual boot with windows, so I have to scroll down for a while to get to it.  And I just like keeping things clean.  So:

1. Can I edit /boot/grub/menu.lst directly or is there another way that I should do it.

2. I'm never going to revert to a previous setting, so really I want to get rid of any storage/backup related to these old settings.  How do I go about cleaning that up as well?

Thanks.

---

### Post by Blindraven on 2008-01-04
sudo vim /boot/grub/menu.lst

Remove the entries.
I highly suggest leaving the second most up to date entry, but its your call.

---

### Post by kpkeerthi on 2008-01-04
Removing the entries from menu.lst will still keep the kernels in your disk wasting space. Search for the kernels that you don't need in Synaptic and remove them. This should also remove the corresponding entries from grub.

---

### Post by yabbadabbadont on 2008-01-04
```
sudo apt-get --purge remove linux-image-<version to be removed>
```

---

### Post by geirha on 2008-01-04
You can also change the number of ubuntu entries it should display by changing the line ```
# howmany=all
``` to ```
# howmany=2
``` for example. (Non-ubuntu entries does not "count")

Run ```
sudo update-grub
``` to have the change take effect

---

### Post by kpkeerthi on 2008-01-04
> 
2. I'm never going to revert to a previous setting, so really I want to get rid of any storage/backup related to these old settings. How do I go about cleaning that up as well?

Please do not confuse the OP. He clearly mentions he wants to get rid of it and recover space. So uninstalling the kernel(s) using apt-get or synaptic is what he needs.

---

