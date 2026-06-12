---
title: "Force boot from a usb"
date: 2020-05-29
forum: General Help
---

### Post by joeyisneat on 2020-05-29
I need to reinstall windows on my current os ubuntu 20. i cant access my bios on my pc because my bios are broken. I was wondering if there was any way i could force a boot from my usb device without having to access bios or grub(i cannot enter grub even if i press  the needed keys to get in).

---

### Post by CatKiller on 2020-05-29
You can use ```
sudo systemctl reboot --firmware-setup
``` to boot into the setup to change the boot order or, for example, turn off fast boot.

---

### Post by lazyteddy on 2020-05-29
Is there a hotkey you can use during start up? The two desktops and the two laptops we have around here all have a way to manually select the boot device. My desktop with an MSI board for example tells me during the boot messages to press F11 to select boot device; on my Dell laptop I have to hit ESC first and then there's another key to get to either bios or the boot device selection.

---

### Post by CatKiller on 2020-05-29
> **lazyteddy said:**
> Is there a hotkey you can use during start up?

From their (admittedly limited) description of the symptoms it seems likely to me that either they've got Fast Boot turned on (so the UEFI will skip hardware detection and input polling) or they don't have support enabled for {USB, Bluetooth} keyboards in the pre-OS environment.

Either of those would give the symptoms they say are present: "i cant access my bios on my pc because my bios are broken," i cannot enter grub even if i press the needed keys to get in."

---

### Post by joeyisneat on 2020-05-29
Hey, i typed the line of code and i got to the boot menu but my keyboard was not working when i pressed anything. do you have any ideas why or how to fix it? btw i have a hp z420 computer

---

### Post by CatKiller on 2020-05-29
> **joeyisneat said:**
> i got to the boot menu but my keyboard was not working when i pressed anything. 
So that symptom is this one:
> **CatKiller said:**
> or they don't have support enabled for {USB, Bluetooth} keyboards in the pre-OS environment.
There's a setting that will let the UEFI load sufficient drivers for making (some) input devices work even without an operating system running. Obviously the issue is that you need an input device that *doesn't* need that emulation before you can enable that setting. A computer of that vintage might be expecting a PS/2 keyboard, but you might get away with a simple USB one in the right port.

---

### Post by lazyteddy on 2020-05-30
> **CatKiller said:**
> So that symptom is this one:

There's a setting that will let the UEFI load sufficient drivers for making (some) input devices work even without an operating system running. Obviously the issue is that you need an input device that *doesn't* need that emulation before you can enable that setting. A computer of that vintage might be expecting a PS/2 keyboard, but you might get away with a simple USB one in the right port.
Can't say I saw this coming. It's been a long time since I had a computer that didn't support USB keyboards during boot; we have a desktop from 2006 sitting around here that I still use on occasion, and it works just fine no matter which port I plug the keyboard in. I *never* would have thought of this.

---

### Post by CatKiller on 2020-05-30
Many keyboards come with a USB-PS/2 adaptor. That might be sufficient in those cases.

---

