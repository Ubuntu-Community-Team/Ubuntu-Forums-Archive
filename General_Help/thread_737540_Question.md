---
title: "Question"
date: 2008-03-27
forum: General Help
---

### Post by rogerdpenguin on 2008-03-27
My hard drive died, I got a new one, and I want to reinstall wubi. Can I install it to an external hard drive, and if I can/do, and I boot without the external hard drive plugged in, what will happen? If I set the boot for boot from removable disk, and the external hdd that has wubi installed isn't plugged in, will the bootloader still show, or will it just boot straight to windows xp?

---

### Post by ago on 2008-03-27
> **rogerdpenguin said:**
> My hard drive died, I got a new one, and I want to reinstall wubi. Can I install it to an external hard drive, and if I can/do, and I boot without the external hard drive plugged in, what will happen? If I set the boot for boot from removable disk, and the external hdd that has wubi installed isn't plugged in, will the bootloader still show, or will it just boot straight to windows xp?

Wubi will add an entry to the windows bootloader on the fixed drive (where you have windows). If the other drive is not there you will still be shown the dual-boot menu, and you will still be able to select windows. But obviously, without the removable drive Ubuntu will not be able to boot.

---

### Post by rogerdpenguin on 2008-03-27
Thanks for your help.

---

