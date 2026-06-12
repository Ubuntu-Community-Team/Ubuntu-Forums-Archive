---
title: "Keyboard and touch pad lock up."
date: 2008-01-17
forum: General Help
---

### Post by DiddyWolf on 2008-01-17
I'm currently running Gutsy on my Compaq v2000 laptop.

I've been having a problem, where every so often, the keyboard and trackpad on my laptop seem to lock up. The system is still running, and in fact, I can plug in a USB mouse and still use the computer. I don't have a USB keyboard available to try that.

I'm not sure what the cause is. Some times it locks up as i'm typing, some times it's while I'm just using the mouse, some times neither.

Does anyone know why this happens? I'd at least like to know if there is anything I can run to reset the keyboard in some way other then restart X (which I haven't confirmed to fix it, I don't know how to restart X with just a mouse), or restart the whole system?

Thanks,

--DiddyWolf

---

### Post by anthonyJC on 2008-01-18
i've got a suggestion for trying yet it doesn't make sense unless your laptop has bios based, non-acpi power saving. in bios change setting of option called usb keyboard/mouse emulation (enabled to disabled.) my thinking being if your keyb/mouse are on ps2,   maybe bios is powering off usb controller(doing ps2 emulation) to save power.   all controllers sit on pci wiring.  it just seems like the only possibility w/o examining syslog. do  laptop manufacturers put keyb/mous on usb internally instead of legacy ps2? i could be true if you have two usb controllers-one for the devices that lock up and one for user use.

---

### Post by DiddyWolf on 2008-01-21
I've determined that it's not X. I've been able to restart X with a USB mouse and the keyboard and track pad were still locked up. The keyboard and touchpad are PS/2 devices. Is there anywhere i should check for any error messages?

---

