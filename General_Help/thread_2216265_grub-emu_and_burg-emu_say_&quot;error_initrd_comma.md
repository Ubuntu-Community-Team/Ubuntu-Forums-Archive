---
title: "grub-emu and burg-emu say &quot;error: initrd: command not found"
date: 2014-04-10
forum: General Help
---

### Post by blake-hipps on 2014-04-10
I installed BURG, but I didn't really like it, so I tried to edit it with grub-customizer. It didn't really work, and I installed super-boot-manager, and removed BURG and installed GRUB again. Now, when I run grub-emu, I select elementary OS or Ubuntu Trusty, and it gives the error "initrd: command not found", and something about loading vmlinuz. So I reinstalled BURG, and burg-emu gave me the same error grub-emu did. Is it just the emulator doing that, or GRUB and BURG itself not being able to load? Please help, I am afraid to reboot.

---

### Post by grumblebum2 on 2014-04-11
grub-emu works here for testing the menu.
I need to focus the terminal though to be able to cycle through the menu.
It will fail if you try to actually boot anything as in the second pic.

---

### Post by blake-hipps on 2014-04-11
This is my GRUB using grub-emu. I dual-boot Luna and Trusty.
When I try to go to Luna.
Same thing happens when I try to boot Trusty.

---

### Post by grumblebum2 on 2014-04-11
If you hit enter on a boot entry it will fail which would be 
expected for grub-emu.

PS I use a background image in grub but it doesn't show in grub-emu.
Do you have an entry in /etc/default/grub for your image?

---

### Post by blake-hipps on 2014-04-11
Yes, but I used grub-customizer, not directly editing it.

---

### Post by blake-hipps on 2014-04-11
So, am I safe to reboot anytime without having super-grub-disk on a flash drive just in case?

---

### Post by grumblebum2 on 2014-04-11
Looks ok, only one way to find out.

---

