---
title: "boot issue"
date: 2018-02-24
forum: General Help
---

### Post by cmcanulty on 2018-02-24
I am getting errors now that sound ominous. Also seeing lilo not grub at boot I ran boot repair successfully but still get the following error and can't find the missing vmlinux in synaptic.  The FATAL below is scary. I do boot OK Thank you

```
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Setting up initramfs-tools (0.122ubuntu8.10) ...
update-initramfs: deferring update (trigger activated)
Processing triggers for initramfs-tools (0.122ubuntu8.10) ...
update-initramfs: Generating /boot/initrd.img-4.4.0-116-generic
Added Linux  +  *
Fatal: open /boot/vmlinuz-4.4.0-109-generic: No such file or directory
run-parts: /etc/initramfs/post-update.d//runlilo exited with return code 1
dpkg: error processing package initramfs-tools (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 initramfs-tools
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

### Post by oldfred on 2018-02-24
Lilo is often used as a Windows boot loader replacement in MBR. Unless you manually installed the full Lilo boot loader to boot in place of grub.

 May be best to see details, you can run from your Ubuntu live installer or any working install, use ppa version not older Boot-Repair ISO:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) and:
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by cmcanulty on 2018-02-24
Boot repair and uninstalling lilo fixed it. Wierd thing is I didn't install lilo and I saw another post  somewhere that had same issue. Lilo must have come in with some other package as I only run xubuntu and always have used grub. Thank you

---

