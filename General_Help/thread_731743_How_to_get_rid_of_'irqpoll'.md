---
title: "How to get rid of 'irqpoll' ?"
date: 2008-03-22
forum: General Help
---

### Post by wisekki on 2008-03-22
I just installed Ubuntu 7.10 x64 to my new comp and when i tried to boot up
for the first time it started saying: 

"ata3.00: Failed to set xfermode (err_mask=0x40)" 

I managed to boot Ubuntu when I added 'irqpoll' to the boot options in grub-menu,
but that fuqr made my comp very slow. I don't know what this irqpoll does or is but even
unrarring takes a very long time. Every hdd response is lagging. Don't know if it affects
anything else...

So my server upgrade wasn't really an upgrade.. it's running slower than my older server :confused:

What do i have to do to get rid of this irqpoll and start enjoying my new 45nm server :)

Cheers, 
 
 Andy

---

### Post by geraldm on 2008-03-23
irqpoll has some advantages when there are problems or conflicts assigning irq interrupts. 
Find out which, if any, interrupts need to be reassigned, and what reassignments can work.
You can remove irqpoll from the grub kernel line and test it, but it is usually put there when some other problem exists. so expect a possible problem to fix.

I do not have any information on the ata3.00 line

Gerald

---

### Post by wisekki on 2008-03-23
I really can't remove the irqpoll from the grub kernel line because Ubuntu won't start at all.
Even if i wait a long time.. it just keeps pasting that ata3.00 line (and even that keeps
changing from ata1 to ata3)

Not sure how to find out which irq's need to be reassigned?
This is what /proc/interrupts say:> 

           CPU0       CPU1       
  0:   27272498   27274332   IO-APIC-edge      timer
  1:          2          0   IO-APIC-edge      i8042
  8:          0          0   IO-APIC-edge      rtc
  9:          0          0   IO-APIC-fasteoi   acpi
 12:          1          3   IO-APIC-edge      i8042
 16:   11396406   11394849   IO-APIC-fasteoi   uhci_hcd:usb1, nvidia
 17:      98382      98999   IO-APIC-fasteoi   libata
 18:   25572119   25567112   IO-APIC-fasteoi   uhci_hcd:usb6, ehci_hcd:usb7, eth1
 19:    4363205    4363607   IO-APIC-fasteoi   uhci_hcd:usb3, uhci_hcd:usb5, libata, libata
 21:    2070056    2071831   IO-APIC-fasteoi   uhci_hcd:usb2, ohci_hcd:usb11
 22:    8549404    8551567   IO-APIC-fasteoi   ehci_hcd:usb9, eth0, HDA Intel
 23:          0          0   IO-APIC-fasteoi   uhci_hcd:usb4, ehci_hcd:usb8, ohci_hcd:usb10
NMI:          0          0 
LOC:   54548190   54548177 
ERR:          0


Lot of devices sharing the same irq.. is this normal? :)
I read somewhere that 'noacpi' -option would help but don't I need that for 
enabling 2 cores from my cpu?

Cheers,
 
- Andy

---

