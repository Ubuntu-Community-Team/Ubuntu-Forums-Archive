---
title: "Ubuntu won't load after Wubi Installation"
date: 2007-10-15
forum: General Help
---

### Post by The Sk on 2007-10-15
Ok well as the title says I installed Ubuntu with Wubi. Unfortunately After my Pc restarted twice, Ubuntu doesn't load. It does ask me what OS to pick. I choose Ubuntu. It shows the Ubuntu Logo and a progress Bar. Then after the progress Bar finishes it goes blank. just into a blank screen. I tired again but nothing. I remember after I restarted My pc out of Xp, and when it went into the installation. a message popped up saying,

Invalid KPBL Length. Then something about some raid disks not being found then it went into the installation. 

If anyone can help it will be greatly appreciated. Thank you all. I really want Ubuntu, I'm sick of XP. :)

---

### Post by ago on 2007-10-15
If you see the ubuntu logo on black screen with orange progress bar, and it hangs after that it is either that you ACPI is not compatible, or that your video card needs a dedicated driver.

If you can press Alt+F2 and get a terminal it is likely the second case. Search this forum for solutions.

---

### Post by The Sk on 2007-10-15
I think its the ACPI. Because it said ACPI:Invalid KPBL Length. How do I fix that. I'll check with the ALT+F2. I uninstalled it so now I have to install it again :(. Lol.

---

### Post by The Sk on 2007-10-16
> **The Sk said:**
> I think its the ACPI. Because it said ACPI:Invalid KPBL Length. How do I fix that. I'll check with the ALT+F2. I uninstalled it so now I have to install it again :(. Lol.

Yea I checked with ALT+12 and I didn't get a terminal. How do I fix the ACPI thing?

---

### Post by ago on 2007-10-16
Append "acpi=off" to the ubuntu/disks/boot/grub/menu.lst and ubuntu/install/boot/grub/menu.lst to each line that starts with "kernel" (before " -- ")

---

