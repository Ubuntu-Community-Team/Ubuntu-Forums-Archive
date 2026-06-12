---
title: "686 acpi=force equals no Power Management?"
date: 2006-07-25
forum: General Help
---

### Post by eXisor on 2006-07-25
First post here so be kind... I'm trying to understand.

I have the 686 shutdown problem with my old m/b (which only supports apm), but can shut down if I set acpi=force on the kernel boot. (I saw that solution in another thread).

Basically,

    boot/vmlinuz-2.6.15-26-686 root=/dev/hda1 _acpi=force_ _apm=on_ quiet ro splash

The apci=force shuts the system down with the 686 kernel. 

But... 

I suspect I am getting NO Power Management at all now, since a 'dmesq | grep apm' says

 - apm is overridden by acpi
 
and a 'dmesq | grep acpi' says 

 - ibm_acpi: ec object not found
 - pcc_acpi: loading...

and it never does load. So maybe all acpi is now doing is just the shutdown?

If there is no power management happening then this shutdown workaround is a surefire way to age your laptop/desktop real pronto, nevermind the energy wasting it implies.

Any thoughts regarding this 'logic' appreciated.

---

