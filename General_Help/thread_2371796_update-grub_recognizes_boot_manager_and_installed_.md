---
title: "update-grub recognizes boot manager and installed linux partition outside chroot"
date: 2017-09-18
forum: General Help
---

### Post by kerrygee on 2017-09-18
Hi,

i am chroot'ing into a remastering environment to modify a unpacked iso image with Cubic: [https://launchpad.net/cubic](https://launchpad.net/cubic)

Whenever i do install some kernel packages in the chroot environment or the apt update process does, the update-grub script detects the host systems devices and generates corosponding entries:

root@devsys:~# update-grub
Grub-Konfigurationsdatei wird generiert ?
Warnung: Werte ungleich 0 für »GRUB_TIMEOUT« werden, falls »GRUB_HIDDEN_TIMEOUT« aktiviert ist, nicht mehr unterstützt.
Linux-Abbild gefunden: /boot/vmlinuz-4.10.0-35-generic
initrd-Abbild gefunden: /boot/initrd.img-4.10.0-35-generic
  /run/lvm/lvmetad.socket: connect failed: Datei oder Verzeichnis nicht gefunden
  WARNING: Failed to connect to lvmetad. Falling back to internal scanning.
Windows Boot Manager auf /dev/sda2@/efi/Microsoft/Boot/bootmgfw.efi gefunden
Ubuntu 16.04.3 LTS (16.04) auf /dev/sda5 gefunden
Adding boot menu entry for EFI firmware configuration
erledigt  

I pretty much guess, that this is the mounted /dev directory from the host into the guest chroot. But how can i avoid this, so that the chroot doesnt see the linux partition and efi firmware outside the chroot environment?

tia

K.

---

### Post by deadflowr on 2017-09-18
Try turning off  os-prober:
open /etc/default/grub in an editor and add
```
GRUB_DISABLE_OS_PROBER="true"
```
and save.

---

### Post by kerrygee on 2017-09-18
> **deadflowr said:**
> Try turning off  os-prober:
open /etc/default/grub in an editor and add
```
GRUB_DISABLE_OS_PROBER="true"
```
and save.

Looks like its working. 

Thank you!

best

K.

---

