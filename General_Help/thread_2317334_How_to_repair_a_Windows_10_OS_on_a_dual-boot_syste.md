---
title: "How to repair a Windows 10 OS on a dual-boot system with Ubuntu 15.10"
date: 2016-03-15
forum: General Help
---

### Post by Kim_Holder on 2016-03-15
I installed Windows 10 alongside Ubuntu 15.10 and have been really happy how the two work together, I can even see the Windows partition from inside Ubuntu and move files back and forth. But the Windows install is broken. I think it was updating and i restarted the machine, i'm not sure though. At any rate, Windows gives me a screen now saying it can't start.

There is a way to go from there to getting it to reinstall from the CD, but maybe that would mess up Ubuntu. Is there a way to do this through Ubuntu?

This is a 64 bit system, and it is a UEFI install.

---

### Post by grahammechanical on 2016-03-15
You can certainly re-install Windows 10 but it will most definitely over-write the Ubuntu boot loader (Grub) and if you are not careful the re-installation might over-write your Ubuntu partitions.

I have no experience installing or re-installing Windows 10 but if you succeed in doing it without wiping Ubuntu then you will need Boot Repair to re-install the Ubuntu boot loader.

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Regards.

---

### Post by oldfred on 2016-03-15
With UEFI, you should be able to go to UEFI or to one time boot key like f10 or f12 and directly boot.
Grub will only boot Working Windows and Windows updates may turn hibernation or the fast start back on. 
And if hibernated grub will not boot Windows. But use UEFI and boot Windows and turn off fast start.

And as grahammechanical says Windows may overwrite grub. With UEFI, it does not actually overwrite it like with BIOS, but does reset UEFI boot order, so Windows is first in boot order.

---

### Post by Kim_Holder on 2016-03-15
I'm going to sit on this until at least the weekend, when it's less of an issue if i have to reinstall ubuntu and reload everything. Thanks for the tips.

---

