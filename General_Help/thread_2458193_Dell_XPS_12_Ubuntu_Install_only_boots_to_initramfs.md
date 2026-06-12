---
title: "Dell XPS 12 Ubuntu Install only boots to initramfs"
date: 2021-02-18
forum: General Help
---

### Post by trimmerguy on 2021-02-18
Hi.

Had a great install but after restarting, it only boots into initramfs. fsck on both partitions found nothing.  Disabled Secure boot and UEFI and enabled legacy boot to install but playing with different boot settings, I get no bootable disk at all.  Any suggestion would be great.

Thanks
Guy

---

### Post by CelticWarrior on 2021-02-18
Welcome.

Disabling Secure boot, yes. It's often suggested to disable it although not mandatory.
Legacy? NO!

Install in UEFI mode in any UEFI hardware, i.e., any 10 years old or newer computer. And in any case installing in one mode and then changing it to the other is guaranteed to NOT boot. So, please check your UEFI ("BIOS") settings, set UEFI mode only with Secure Boot and Fast Boot off, whenever applicable.

---

### Post by trimmerguy on 2021-02-18
That worked.  I appreciate your clear explanation.  Once I enabled UEFI and turned off Secure Boot and than reinstalled on those settings.  I have not seen an issue after several reboots.  Thank you very much.

Guy

---

