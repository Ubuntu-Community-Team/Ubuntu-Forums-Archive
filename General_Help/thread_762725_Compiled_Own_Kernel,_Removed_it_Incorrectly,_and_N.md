---
title: "Compiled Own Kernel, Removed it Incorrectly, and Now Your Hosed? Read."
date: 2008-04-22
forum: General Help
---

### Post by mlapaglia on 2008-04-22
I made my own kernel, which didn't work too well. I thought I had uninstalled it properly, but on the next system update I ran I couldn't finish it. I was told to run ```
dpkg --configure -a
```. When I did this, I got an error:

```
root@amanda-laptop:/boot# sudo dpkg --configure -a
Setting up initramfs-tools (0.85eubuntu36) ...
update-initramfs: deferring update (trigger activated)

Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.25-custom
Cannot find /lib/modules/2.6.25-custom
update-initramfs: failed for /boot/initrd.img-2.6.25-custom
dpkg: subprocess post-installation script returned error exit status 1

```

I read through a few tutorials and ran:

```
root@amanda-laptop:/boot# update-initramfs -k 2.6.25-custom -d -v
Cannot delete /boot/initrd.img-2.6.25-custom, doesn't exist.

```

but the file wasn't there (I deleted it incorrectly.) So I *created* a initrd.img-2.6.25-custom through gedit, then saved it, then re ran the command, which completed successfully. Then I reran "dpkg --configure -a", which completed successfully.

I hope this helps someone :)

---

