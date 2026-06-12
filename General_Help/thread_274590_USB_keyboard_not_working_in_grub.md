---
title: "USB keyboard not working in grub"
date: 2006-10-10
forum: General Help
---

### Post by cronholio on 2006-10-10
I got a new Speedlink Illuminated USB keyboard and it works in Dapper. I can also enter the BIOS menu by pressing F2 when booting. However, I cannot get into the Grub menu by pressing ESC, because the keyboard driver obviously isn't loaded at that time. Is there any way to tell Grub about the keyboard or do I have to use a PS/2 keyboard each time I want to boot another kernel or "the other OS" (God forbid that the day may come)?

---

### Post by robinl on 2006-10-10
It should be something about BIOS setting, try turning on (or off) the "legacy USB keyboard support" or something similar in the BIOS.

---

### Post by woekele on 2006-10-10
I have the same problem. If I turn on the legacy support for USB, it gives me other problems (windows not booting at all for example).

It would be nice if grub could just 'read' USB-keyboards without that option. My keyboard works fine in the bios and for other pre-boot stuff (configuring my SATA for example), so I dont see why it wouldn't work in grub.

---

### Post by cronholio on 2006-10-11
It worked for me (of course, I should have thought of that myself). Now it seems that the numpad keys stop working randomly. For now, I can live with that.

---

### Post by r!ots on 2006-11-22
my usb keyboard is working in neither BIOS nor GRUB even if i enable the usb legacy support. until now i used an usb to ps/2 adapter but now i got a new keyboard and that doesn't work with the adapter anymore.

my mainboard is an asus A7V8X. last time i tried to update the BIOS with aflash it didn't work.
does anyone have any ideas how to fix that problem?

---

### Post by cronholio on 2006-11-22
What type of keyboard is it? Did you try to google the keyboard name and "linux"?

---

### Post by r!ots on 2006-11-22
both of my keyboards work in linux. they don't work in the BIOS and the GRUB menu when i plug them in an USB-port.
so i think it has something to do with the usb support of my mainboard. at the moment i'm trying to find out why a BIOS update won't work.

Using EZFlash i get the following error message:

> File size incorrect with flash memory: SST 49LF020.

Any ideas?

---

### Post by ubu-for on 2007-07-03
> **r!ots said:**
> Any ideas?

Try [this](http://ubuntuforums.org/showthread.php?t=490854&highlight=grub+usb+keyboard) with another keyboard.

---

