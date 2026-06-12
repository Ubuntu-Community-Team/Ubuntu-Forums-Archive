---
title: "&quot;Dead&quot; keyboard at login"
date: 2008-02-11
forum: General Help
---

### Post by Thies on 2008-02-11
Hi folks!
Strange thing on a clean, new install of Ubuntu 7.10 (i386): My keyboard is "dead" at the Gnome login-screen. Mouse is working fine. Booting in recovery-mode works fine too (keyboard is available here).
Any ideas ?!
Many thanks in advance,
/Thies

---

### Post by DillyP on 2008-02-11
Is it a USB or PS/2 keyboard?  I had some problems with my USB keyboard being dead when I had other USB devices plugged in at boot- namely a couple of external hard drives.

---

### Post by Thies on 2008-02-11
> **DillyP said:**
> Is it a USB or PS/2 keyboard?  I had some problems with my USB keyboard being dead when I had other USB devices plugged in at boot- namely a couple of external hard drives.
It's a "oldy but goldy" PS/2 keyboard ...

---

### Post by harr986 on 2008-02-12
Had Gutsy running fine. Was working on getting internet streaming working. finally late 2-10 got it working. Shut down. Rebooted 2-11 and found keyboard dead at login screen. PS2 keyboard, usb wireless mouse, the mouse still works. If I select boot to terminal from the options the keyboard remains dead. If I select (rescue mode)?? in grub I still have a dead keyboard. Keyboard works when Windows is booted.

---

### Post by Thies on 2008-02-12
I changed now a bit my hardware and the PS/2 keyboard & USB mouse are replace by a USB keyboard/mouse thingy.
I noticed that updating my nVidia video card (restricted) driver actually was responsible for this. I used Envy to update the driver and after reboot was the keyboard was dead at the GDM login screen. So I rebooted in rescue mode and changed back my X11 settings. After this all workd fine again, but I'm still lacking 3D support for my graphic card. :(
I will try next with the nvidia-legacy driver from the repos. 8-[

---

### Post by SurrealWraith on 2008-02-12
> **DillyP said:**
>  I had some problems with my USB keyboard being dead when I had other USB devices plugged in at boot.

Thank you for this advice.  Although my keyboard was PS/2 not USB, when I unplugged all USB devices excluding my mouse, the keyboard worked again.  I do not know what device caused the problem, but thank you none the less.

---

