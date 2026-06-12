---
title: "Usb stick with ubuntu server"
date: 2008-06-15
forum: General Help
---

### Post by dezeGno on 2008-06-15
Hi there.
I just plugged a 2gb usb stick in my server machine and i need to locate it. Where could i find it? 

Thanks for your responses, I'm still learning so don't flame.

---

### Post by sdennie on 2008-06-15
It should be one of the directories in /media.

---

### Post by dezeGno on 2008-06-15
the only things that i find there are cdrom, cdrom0, floppy & floppy0 :S

And thanks for the quick reply :D

---

### Post by Quantumstate on 2008-06-15
Meh, probably don't have support.

Unplug it, plug it, and then in konsole
dmesg

These are your system messages.  Look for evidence at the end that it found a new USB device and probably named it sdb1 or ~such.

If not there, 
lspci

and tell us specifically what kind of MMC controller you have.

---

### Post by prshah on 2008-06-15
> **dezeGno said:**
> Hi there.
I just plugged a 2gb usb stick in my server machine and i need to locate it. Where could i find it? 


Unplug it, wait a few seconds, replug it. Then open a terminal (Applications-Accessories-Terminal), then give the following commands and post the output here. ```

dmesg | tail

```

---

