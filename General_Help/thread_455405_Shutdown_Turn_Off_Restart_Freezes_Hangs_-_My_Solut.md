---
title: "Shutdown Turn Off Restart Freezes Hangs - My Solution"
date: 2007-05-26
forum: General Help
---

### Post by jhanagan on 2007-05-26
I solved my problem of my system hanging at restart/reboot/shut down -  by accident.
I loaded the new proprietary ATI x300 driver using the restricted-package tool, and my system now behaves itself at shutdown and restart.  I don't know if it's cause and effect or dumb luck.
([http://ubuntudaily.blogspot.com/2007/03/proprietary-drivers-in-feisty-not-by.html](http://ubuntudaily.blogspot.com/2007/03/proprietary-drivers-in-feisty-not-by.html))

ASUS A8N motherboard, ASUS/ATI Radeon x300 video card

---

### Post by cyrusrayne on 2007-05-27
Very cool :)  I don't have any theories, but I've had similar experiences.

---

### Post by Belohin on 2007-05-30
Well, I have totally reverse experiences. Before I have installed the ATI driver, I could turn off at least with 'shutdown -h now' in console. After installation this possibility is away too.
(On a desktop PC with ATI video card.)

---

### Post by Crafty Kisses on 2007-05-30
> **jhanagan said:**
> I solved my problem of my system hanging at restart/reboot/shut down -  by accident.
I loaded the new proprietary ATI x300 driver using the restricted-package tool, and my system now behaves itself at shutdown and restart.  I don't know if it's cause and effect or dumb luck.
([http://ubuntudaily.blogspot.com/2007/03/proprietary-drivers-in-feisty-not-by.html](http://ubuntudaily.blogspot.com/2007/03/proprietary-drivers-in-feisty-not-by.html))

ASUS A8N motherboard, ASUS/ATI Radeon x300 video card

Nice man, congrats. Keep us updated.

---

### Post by Belohin on 2007-05-30
I have to correct myself. The problem was that update manager has just installed a new kernel version and in the menu.lst there was not any kernel parameter I had taken before.

With acpi=force apm=off parameters and with proprietary ATI driver the system does shutdown now.

---

