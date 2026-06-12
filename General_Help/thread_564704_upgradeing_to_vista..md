---
title: "upgradeing to vista."
date: 2007-10-01
forum: General Help
---

### Post by 127.0.0.1 on 2007-10-01
well i am upgradeing to windows vista today with a clean installation, i was woundering that if i install vista, it will install lilo boot loader with it. i am currently useing grub, if i install lilo will i still be able to dural boot ubuntu and vista? or will i need to install grub again? if i do please tell me how. thanks.

I would guess i would configure lilo to boot ubuntu, however ubuntu if currently being booted with grub, and might not work with lilo? :confused:

---

### Post by rsambuca on 2007-10-01
Windows uses its own bootloader, and when you install Vista it will overwrite grub.  After you install Vista, you can easily re-install grub using any Ubuntu liveCD.

---

### Post by 127.0.0.1 on 2007-10-01
> **rsambuca said:**
> Windows uses its own bootloader, and when you install Vista it will overwrite grub.  After you install Vista, you can easily re-install grub using any Ubuntu liveCD.

ah, so i would insert a ubuntu live cd and use the fdisk /mbr command? or do i do something elce? lol

---

