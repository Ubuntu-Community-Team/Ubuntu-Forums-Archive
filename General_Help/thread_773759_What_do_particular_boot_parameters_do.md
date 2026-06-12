---
title: "What do particular boot parameters do?"
date: 2008-04-29
forum: General Help
---

### Post by lesliek on 2008-04-29
I installed Ubuntu 8.04 via Wubi on a Dell Inspiron 1501 laptop.

At first, I kept getting shunted into BusyBox when I chose Ubuntu in Grub, but, as a result of reading here, I found that adding the three boot parameters, all_generic_ide, floppy=off and irqpoll, got round that problem.

However, I didn't know whether any of those boot parameters would cause me some problem when running, so, as an experiment, I kept rebooting and choosing different combinations of the three parameters to see the minimum combination that'd work.

First, I tried each of the three on its own. None of them worked on its own.

Next, I tried any two of them together and discovered, much to my surprise that any of the three available combinations of two worked.

Since I have no floppy drive anyway, I assume that I should choose floppy=off as one of my two parameters.

Of the other two, if I had some idea of what they did, maybe it would be obvious that I should use one of them rather than the other.

Can anyone explain to me what all_generic_ide and irqpoll do?

Thanks for reading this.

---

### Post by Vermind on 2008-04-29
Hello,
The irqpoll option has to do with assigning irq numbers to devices.
[A short post on what irqpoll does]("http://ubuntuforums.org/showpost.php?p=2856124&postcount=3"). 
Some highlights:
Booting says:
"Misrouted IRQ fixup and polling support enabled. This may significantly impact system performance."
"irqpoll: When an interrupt is not handled, search all known interrupt handlers for it."

So, irqpoll hurts performance in the sense that if device's interrupts are not handled, it searches all handlers for it, which makes the system slower the more there are requests from devices without properly assigned handlers. There's a related kernel option: pci=routeirq.
Excerpt from: [Linux kernel mailing list]("http://linux.derkeiler.com/Mailing-Lists/Kernel/2004-09/7267.html"):
"[If a ] driver failed to call pci_enable_device() ...
as a temporary workaround, the "pci=routeirq" argument ... 
[causes] ... using ACPI for routing PCI interrupts for all devices."

So, I would recommend doing the all_generic_ide:
[linux questions: can't see hard disk]("http://www.linuxquestions.org/questions/linux-newbie-8/instals-cant-see-hard-disc-562103/"): "you will end up using a generic ide module/driver to access the drive."

---

### Post by lesliek on 2008-04-29
Thanks very much for the information and suggestion, Vermind.

I'll use the all_generic_ide option then (with floppy=off).

Thanks again.

---

