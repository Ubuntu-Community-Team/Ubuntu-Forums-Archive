---
title: "Grub Scren Entry &quot;System setup&quot;?"
date: 2016-02-16
forum: General Help
---

### Post by 2CV67 on 2016-02-16
Since the latest update, I have a new line on my grub screen - System setup.

Is this normal?

What is it for & what should I find there?
I know I could just take a look, but don't feel like accidentally upsetting anything at the moment!
Searching (briefly) didn't find anything.

Thanks!

---

### Post by ajgreeny on 2016-02-16
Perfectly normal, at least if you have a UEFI boot system, though I do not see it in my BIOS boot system of the same version (14.04) of *ubuntu.

---

### Post by Dennis N on 2016-02-16
It reboots the system and then enters the UEFI firmware settings without further user action. Try it and see; you can exit without changes. It can be removed from the menu if desired by changing the executable status of **/etc/grub.d/30_uefi-firmware** to non-executable and then running sudo update-grub.

---

