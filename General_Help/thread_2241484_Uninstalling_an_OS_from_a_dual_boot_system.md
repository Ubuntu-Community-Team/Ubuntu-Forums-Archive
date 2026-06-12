---
title: "Uninstalling an OS from a dual boot system"
date: 2014-08-26
forum: General Help
---

### Post by grantmcduling on 2014-08-26
I have a computer that has ubuntu and peppermint installed. I want to uninstall peppermint. Are there any instructions available to guide me through this?

---

### Post by Impavidus on 2014-08-26
First make sure Ubuntu is the OS controlling the dual boot menu. If you're not sure, boot Ubuntu and run```
sudo grub-install /dev/sda
```to reinstall grub. Replace sda with the drive where you want your boot loader, but usually it's sda.
Then you can delete the Peppermint partition. Just removing the boot files will do, actually. Then run```
sudo update-grub
```to remove Peppermint from the grub menu. Finally find a way to use your reclaimed disk space. Or keep it reserved for the future.

---

