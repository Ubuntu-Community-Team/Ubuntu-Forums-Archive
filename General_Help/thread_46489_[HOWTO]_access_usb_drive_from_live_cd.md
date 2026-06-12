---
title: "[HOWTO] access usb drive from live cd"
date: 2005-07-05
forum: General Help
---

### Post by ch2 on 2005-07-05
i just using the ubuntu live cd and plug in my external usb hdd but it seems like nothing happens and i can't find my usb drive anywhere.

is there any particular step has to be done or any special tricks?

please help me somebody, i trying to access a corrupted sata hdd to save some data.

---

### Post by bihan on 2005-07-05
[QUOTE=ch2]i just using the ubuntu live cd and plug in my external usb hdd but it seems like nothing happens and i can't find my usb drive anywhere.

is there any particular step has to be done or any special tricks?

please help me somebody, i trying to access a corrupted sata hdd to save some data.[/QUOTE]
 hi, 

to find what's happening (or not), type "dmesg" in a console after having plugged your disk. locate the lines "Device attached to /dev/xxx"

that means that your disk as been recognized and that you can mount it from /dev/xxx

If you dont get any line like this, check out if your ohci and ehci modules are loaded via typing "lsmod"


bihan

---

