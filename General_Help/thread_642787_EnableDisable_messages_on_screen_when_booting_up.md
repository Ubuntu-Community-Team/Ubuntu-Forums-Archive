---
title: "Enable/Disable messages on screen when booting up"
date: 2007-12-17
forum: General Help
---

### Post by davidcopper on 2007-12-17
Hi, all.

Can anyone tell me how I can enable/disable messages show up on screen when booting up system ? 

Many thanks.

---

### Post by kpkeerthi on 2007-12-17
**Quick fix:**
Press ALT+F1 when you are at the boot splash.

**Permanent Fix:**

1. edit /boot/grub/menu.lst
2. Locate the kernel boot line 
3. Delete the word **splash**. (Also remove **quiet** if need more verbose messages)
4. Save and reboot.

---

### Post by mikewhatever on 2007-12-17
What messages do you get when booting? Generally, the word quiet as boot parameter disables the showing of boot process. It should be there by default, but do check your grub menu.lst file.

> /boot/vmlinuz-2.6.22-14-generic root=UUID=3ea966c0-8100-4c95-a7ae-57f656fe2b81 ro **quie**t splash

---

### Post by davidcopper on 2007-12-17
Thanks for the quick reply. I prefer to make a permanent change, so I will investigate menu.lst.

---

