---
title: "Installing kernel 2.6.24-17-generic"
date: 2008-05-29
forum: General Help
---

### Post by dlmoak on 2008-05-29
If I update the kernel using Synaptic, will the installation add the kernel to the boot menu or will the old kernel(16) be replaced?  I'm a new user and not up on Linux yet.  Assuming I like the new kernel after I've tried it out and that the old one is still there, if I use Synaptic to remove the old kernel will the boot menu be changed back?

Thanks in advance

---

### Post by FuturePilot on 2008-05-29
Yes, it will just add a new entry for the -17 kernel. You can remove the -16 kernel with Synaptic if you want and it will remove the -16 kernel entry from Grub

---

### Post by drs305 on 2008-05-29
> **dlmoak said:**
> If I update the kernel using Synaptic, will the installation add the kernel to the boot menu or will the old kernel(16) be replaced?  I'm a new user and not up on Linux yet.  Assuming I like the new kernel after I've tried it out and that the old one is still there, if I use Synaptic to remove the old kernel will the boot menu be changed back?

Thanks in advance

During the upgrade, you will be asked if you want to keep your current boot list, which comes up as the default. However, if you do this it may continue to boot with the -16 kernel, which is what you have now. I have upgraded several times and on the last one selected the top option to allow grub to be updated. This makes -17 the default but retains any tweaks you made such as timeouts and kernels to display.

I would recommend you allow it to update grub, but make a backup of your current menu.lst first.

Added: Yes, removing a kernel via synaptic will update menu.lst, but I would not remove the old kernel for a while. You can edit what you see on the menu via startupmanager.

To backup grub:
```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.bak
```

---

### Post by Seisen on 2008-05-29
I recommend that you don't remove the old kernel in case something goes wrong with the new kernel.

---

### Post by dlmoak on 2008-05-29
Thanks so much for the help!  I am really enjoying Ubuntu and the help I've received for the few problems I've had and the answers to questions I've asked has been quite refreshing.

---

