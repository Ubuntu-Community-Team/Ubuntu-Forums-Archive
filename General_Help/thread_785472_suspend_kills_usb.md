---
title: "suspend kills usb"
date: 2008-05-07
forum: General Help
---

### Post by MartinG on 2008-05-07
I don't think this is a 64-bit specific problem, which is why I'm posting here, but it might be? ...

Using Kubuntu 8.04 (though it's the same with a Gnome desktop) with AMD 64 dual-core on an ASRock ALiveNF7G-HD720p R5.0 motherboard, my computer will suspend to RAM fine (I'm not bothered about hibernation).  However, on "wake up" I have no USB.

I've tried removing and reloading ehci_hcd, ohci_hcd, but to no avail.  I've tried including the same in MODULES and/or MODULES_WHITELIST in /etc/acpi-support, I've tried installing the hibernate and/or uswsusp packages.  None of it works, the only way to get USB working again is to reboot :(

---

### Post by Whiffle on 2008-05-07
Have you tried uhci_hcd?  Thats the one for usb1.1

---

### Post by MartinG on 2008-05-11
> **Whiffle said:**
> Have you tried uhci_hcd?  Thats the one for usb1.1
Thanks. No, I hadn't tried it as it's not normally loaded.  I have now tried it, however, with no change :-(

---

