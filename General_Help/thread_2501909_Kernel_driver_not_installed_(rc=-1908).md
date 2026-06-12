---
title: "Kernel driver not installed (rc=-1908)"
date: 2024-10-25
forum: General Help
---

### Post by direwalker on 2024-10-25
Kernel driver not installed (rc=-1908)

The VirtualBox Linux kernel driver is either not loaded or not set up correctly. Please try setting it up again by executing

'/sbin/vboxconfig'

as root.

If your system has EFI Secure Boot enabled you may also need to sign the kernel modules (vboxdrv, vboxnetflt, vboxnetadp, vboxpci) before you can load them. Please see your Linux system's documentation for more information.

where: suplibOsInit what: 3 VERR_VM_DRIVER_NOT_INSTALLED (-1908) - The support driver is not installed. On linux, open returned ENOENT. 

(How do i fix this?)

---

### Post by grahammechanical on 2024-10-25
We are assuming that you have installed VirtualBox but we do not know which version of Ubuntu you are using. Where did you download VirtualBox from? What instructions did you follow? Is secure boot enabled?

What happens when you run

```
sudo /sbin/vboxconfig
```

Regards

---

