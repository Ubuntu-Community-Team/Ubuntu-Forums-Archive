---
title: "Hide all kernel boot messages/logging when disabling splash screen Lubuntu 14.04.1"
date: 2014-09-01
forum: General Help
---

### Post by roler2 on 2014-09-01
In Lubuntu 13.10 I was able to redirect the kernel messages/logging to another tty by adding the following to the Grub file in order to hide all kernel boot messages when disabling the splash screen and it booted very quickly:


GRUB_CMDLINE_LINUX="console=tty12"


 However when I add the same line to Grub in Lubuntu 14.04.1 I still get all of the boot/logging messages, which actually is taking much longer to boot than having the splash screen present. After I added the new parameter and deleted "splash" I did run sudo update-grub and the new parameter was present after updating and also after re-booting and splash was not present. I also tried console=tty6 and console=tty9 and neither worked. I still receive a full screen of boot messages.


The only way to not receive boot messages is to re-add the "splash" parameter.
 


Any assistance would be greatly appreciated. Thank you!

---

