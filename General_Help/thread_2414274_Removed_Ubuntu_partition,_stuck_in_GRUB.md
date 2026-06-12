---
title: "Removed Ubuntu partition, stuck in GRUB"
date: 2019-03-08
forum: General Help
---

### Post by person-a on 2019-03-08
Hi, so I removed the ubuntu partition from my SSD, and now I’m stuck in GNU GRUB. I tried to f12 but it doesn’t do anything, and I have no idea what to do. My system is a 2017 Lenovo laptop if that adds anything. Any help is greatly appreciated

---

### Post by kc1di on 2019-03-08
It would help if we know why you wanted to delete the ubuntu partition and what operating system your trying to boot.  I suspect that grub looked to Ubuntu as that was most likely the last system you installed and you deleted it's config. file so it no longer can boot. Give us a little more info on what your trying to accomplish.

---

### Post by yancek on 2019-03-08
The majority of the Grub boot files used to boot the computer are on the system partition, the one you deleted!  So if you do have another operating system on the computer, the first step would be to make certain that this other OS is set to boot without Ubuntu either by installing the boot code of the other OS to the MBR of your primary drive or setting it to first boot in EFI, if you are using EFI.  You did things backwards but posting more detailed information on what you have would help someone to help you.

---

### Post by Impavidus on 2019-03-08
Try [Boot-Repair](https://help.ubuntu.com/community/Boot-Repair). The BootInfo Summary can tell us what's going on. Depending on what's left on the computer, Boot-Repair may be able to fix it.

---

