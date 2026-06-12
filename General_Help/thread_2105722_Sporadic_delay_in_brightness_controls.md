---
title: "Sporadic delay in brightness controls"
date: 2013-01-16
forum: General Help
---

### Post by hiKen on 2013-01-16
Hello everybody,

My laptop is a Sony Vaio S13 laptop with a Nvidia 310M graphics card. Ever since I installed Ubuntu on it (11.10, now running 12.04) I have been having a recurring problem with the brightness controls. Besides the need to edit /etc/X11/xorg.conf and adding EnableBrightnessControl=1, some times brightness controls are very laggy and unresposive (needs 2 or more key strokes to respond). This really gets on my nerves as it is difficult to get a specific brightness level.

I've found a workaround that consists in generating a new xorg.conf file with nvidia-xconfig, re-adding the brightness line and rebooting, however a few sessions later the problem is back again.

I still have not found when exactly does this happens and how to reproduce it, however it seems to have something to do with power management, as it often starts on the boot after changing from AC power to battery or vice-versa. On the other hand, it may be related to something that happens during boot or shutdown, as I've noticed that it freezes for some seconds when rebooting (not on shutdown) - though this might be a completely unrelated problem.

Does anyone has a similar problem and knows a fix? Any insight on this is useful, I'm lost here...

---

### Post by griffjon on 2013-01-17
This is happening to me on a Dell Latitude E6430 , no Nvidia (Intel graphics), in 12.10, 64bit.  I had to add "acpi_backlight=vendor" to my grub to even get it to work at all, and it worked great for ~20 changes up and down, and now is extremely (30 seconds) lagged.

Here is a launchpad bug that appears related: [https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/847001](https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/847001)

---

### Post by hiKen on 2013-01-18
> **griffjon said:**
> This is happening to me on a Dell Latitude E6430 , no Nvidia (Intel graphics), in 12.10, 64bit.  I had to add "acpi_backlight=vendor" to my grub to even get it to work at all, and it worked great for ~20 changes up and down, and now is extremely (30 seconds) lagged.

Here is a launchpad bug that appears related: [https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/847001](https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/847001)

I'll try adding that line to GRUB, but I don't think it is the same issue. While this does not happen constantly, when it does happen the delay is ust about 3 seconds, but it requires more than one key stroke for it to react, which makes it difficult to set a specific brightness level.

---

### Post by hiKen on 2013-01-31
> **griffjon said:**
> This is happening to me on a Dell Latitude E6430 , no Nvidia (Intel graphics), in 12.10, 64bit.  I had to add "acpi_backlight=vendor" to my grub to even get it to work at all, and it worked great for ~20 changes up and down, and now is extremely (30 seconds) lagged.



Adding "acpi_backlight=vendor" didn't solve my problem, in fact it completely disabled the brightness control keys.

Anyone with further suggestions?

---

### Post by hiKen on 2013-02-22
Noone has the same problem? It seems to me that is related to either the nvidia drivers or the acpi services under AC or battery power....

---

### Post by kas21 on 2013-06-28
I too am having this issue with 13.04 on my Latitude E6430 (Intel graphics).  Did anyone resolve the problem?

---

