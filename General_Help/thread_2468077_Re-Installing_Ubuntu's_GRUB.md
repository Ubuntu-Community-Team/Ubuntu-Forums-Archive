---
title: "Re-Installing Ubuntu's GRUB"
date: 2021-10-17
forum: General Help
---

### Post by tb75252 on 2021-10-17
I have Ubuntu 21.10, 64-bit.
I recently installed a second Linux OS (Fedora).  Without warning, Fedora overwrote the GRUB version that Ubuntu had installed in the MBR (/dev/sda - my PC does not have EFI/UEFI).
I like Ubuntu's GRUB version better, so I would like to know how to re-install it in the MBR.
Thanks.

---

### Post by oldfred on 2021-10-17
Fedora's grub should let you boot Ubuntu.
Then in Ubuntu reinstall grub.
sudo grub-install /dev/sda

Note major updates to grub will reinstall grub. So Fedora may reinstall again if it gets a major update.
You just have to maintain it.

If you can boot Fedora from Ubuntu, which you should you may be able to turn off updates to grub in Fedora.
If you used LVM in Fedora you will need the lvm2 driver in Ubuntu which is removed from an install unless install uses LVM.

---

### Post by guiverc on 2021-10-17
> **oldfred said:**
> 
Note major updates to grub will reinstall grub. So Fedora may reinstall again if it gets a major update.
You just have to maintain it.


I agree 100% with @oldfred, however in my experience it's the installs only that cause grub stage 0 (the MBR) to be overwritten.

I have systems with Debian, openSuSE, Fedora & more, and it's only installs that usually cause another OS (*last-installed*) to take ownership of the sector 0/MBR of a disk. 

If I recall correctly; even the switch from Fedora 33 to Fedora 34 (*which required reboot*) needed me to do an extra reboot because **I** was too slow & it booted to my default (Ubuntu) - because even the *Fedora release-upgrade* didn't take ownership away from my chosen Lubuntu/Ubuntu.  But things may change; so oldfred's comment is valid.

---

### Post by tb75252 on 2021-10-18
> **oldfred said:**
> Fedora's grub should let you boot Ubuntu.
Then in Ubuntu reinstall grub.
sudo grub-install /dev/sda

Note major updates to grub will reinstall grub. So Fedora may reinstall again if it gets a major update.
You just have to maintain it.

If you can boot Fedora from Ubuntu, which you should you may be able to turn off updates to grub in Fedora.
If you used LVM in Fedora you will need the lvm2 driver in Ubuntu which is removed from an install unless install uses LVM.
Everything went fine.  Thanks for your help.

---

