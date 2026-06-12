---
title: "Boot loop after fresh install"
date: 2022-12-26
forum: General Help
---

### Post by DuckDodgers on 2022-12-26
I just installed Ubuntu Jamming Jellyfish on my Wacom mobile studio 13. When I turn on the computer it starts a boot loop. I can press f12 to get what I thought should be Grub which show two boot options

Phision ESMP512GMB4702-E197
and
ubuntu (Phision ESMP512GMB4702-E197)

If I choose the second option it will boot just fine, but I can't seem to change the boot order so it starts with the Ubuntu version first. The grub customizer doesn't even list the two options I get when I press f12 during a boot.

Does anyone know what is going on, or how I might fix this issue?

---

### Post by tea for one on 2022-12-27
Grub-customizer changes the contents of some grub folders and, when it doesn't perform as expected, it is very difficult to offer suitable solutions.
More info here [https://easylinuxtipsproject.blogspot.com/p/grub-customizer.html](https://easylinuxtipsproject.blogspot.com/p/grub-customizer.html)

Secondly, it may be a good idea to pose your question on the appropriate Launchpad site [https://launchpad.net/grub-customizer](https://launchpad.net/grub-customizer)

---

### Post by ajgreeny on 2022-12-27
Did you make any changes to grub when you used grub-customiser and if so what were they?

I suspect that the F12 key is simply the UEFI/BIOS device priority key and will therefore never make any changes to grub.
Do you actually see a grub menu when you boot or does it go straight to the device menu that you mentioned?

---

### Post by DuckDodgers on 2022-12-29
It turns out that my computer was using EFI to boot which I was able to figure out how to edit here:

[https://askubuntu.com/questions/325048/cleaning-up-and-changing-the-efi-boot-order-permanently-using-eifbootmgr](https://askubuntu.com/questions/325048/cleaning-up-and-changing-the-efi-boot-order-permanently-using-eifbootmgr)

Thank you all for your input.

---

