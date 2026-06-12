---
title: "Kernel Panic"
date: 2004-11-17
forum: General Help
---

### Post by mooncutter on 2004-11-17
Ubuntu was crashing overnight for me, so I looked through the forums and found to add 'noapic nolapic' into grub.lst.  When I rebooted, I got: 
```
Fatal Exception in Interrupt: Interrupt Handler not syncing
``` 
I rebooted again, and went to the grub editor menu and removed the options I had added (as well as trying the 386 kernel boot that I hadn't edited).  I'm still getting the same error! Help!

---

### Post by dataw0lf on 2004-11-17
I was having a similar problem, I'm not sure, but I think whats happening is acpi is screwing up some IRQ values.  Try resetting your IRQs in your BIOS.
dataw0lf

---

### Post by FLeiXiuS on 2004-11-17
[QUOTE=mooncutter]Ubuntu was crashing overnight for me, so I looked through the forums and found to add 'noapic nolapic' into grub.lst.  When I rebooted, I got: 
```
Fatal Exception in Interrupt: Interrupt Handler not syncing
``` 
I rebooted again, and went to the grub editor menu and removed the options I had added (as well as trying the 386 kernel boot that I hadn't edited).  I'm still getting the same error! Help![/QUOTE]



I've received this error with a lot of motherboards which weren't supportive.  Take a look at the wiki.

[http://www.ubuntulinux.org/wiki/HardwareSupport](http://www.ubuntulinux.org/wiki/HardwareSupport)

---

