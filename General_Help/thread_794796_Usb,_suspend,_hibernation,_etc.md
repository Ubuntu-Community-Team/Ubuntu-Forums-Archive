---
title: "Usb, suspend, hibernation, etc"
date: 2008-05-15
forum: General Help
---

### Post by monestri on 2008-05-15
Exhausted with ubuntu and all the problems. Tried since fiesty to fix them. 

1. HIbernation, suspend problems. Close laptop, open it later. Mouse point is gone (mouse still works). synaptics touchpad is messing up, scroll wheel stops working, mousepad still works. 
2. idle for 10 mins = black screen, hangs/freezing.
3. OMG USB gaaaaa. plugged in at boot works. hotswapping does not. NO response from dmesg when trying to hotswapp so it isn't an automount issue (as manual mount wouldn't work anyway). 

above are the most basic issues. just thought i'd make a single thread 'cause i've given up on looking. feel free to ask for extra information if you think you can help. thanks

---

### Post by zenwalker on 2008-05-15
Seems like u r comp got a buggy ACPI. Try disabling it, but yes u will lose hibernation/suspend feature. 

And idle for 10Mins, is coz of the Power Mgmt feature. Again it uses ACPI (APM) feature of u r BIOS.

---

### Post by monestri on 2008-05-15
does this have anything to do with noapic no1apic i use when installing ubuntu?

as for acpi, do I disable this in bios? I'm not sure i've ever seen an option like that.

> **zenwalker said:**
> Seems like u r comp got a buggy ACPI. Try disabling it, but yes u will lose hibernation/suspend feature. 

And idle for 10Mins, is coz of the Power Mgmt feature. Again it uses ACPI (APM) feature of u r BIOS.

---

### Post by monestri on 2008-05-15
adding acpi=off to the kernel line in grub causes problems in boot. any other suggestions?

---

