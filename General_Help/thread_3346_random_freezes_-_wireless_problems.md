---
title: "random freezes - wireless problems?"
date: 2004-11-05
forum: General Help
---

### Post by adamvert on 2004-11-05
Hi

I installed Ubuntu last weekend, and so far I'm totally impressed: most things just worked out of the box on my Toshiba Satellite M30 Centrino laptop.

But I've got a problem now of random freezing.  Every now and then, the computer will just stop responding.  Screen remains the same, but nothing happens, and I have to hit the power switch to reboot.

I've got a feeling this *might* be to do with my wireless connection, but I'm not 100% sure.  I have a Linksys ADSL Gateway that is prone to randomly dropping the wireless connection, and I'm wondering whether this is what's causing the freezes.  Is it possible that this could actually freeze up the computer?  And is there any way of finding out for sure whether this is the problem?

(I know the obvious answer is to turn off the wireless connection, but I kind of need it to work, so I'd rather try some other approaches if anyone has any ideas)

TIA!
Adam

---

### Post by diebels on 2004-11-05
You could try putting "noapic nolapic" kernel parameters in /boot/grub/menu.lst. The line with "kernel          /boot/vmlinuz-2.6.8.1-3-686 root=/dev/hda1 ro quiet splash", change to "kernel          /boot/vmlinuz-2.6.8.1-3-686 root=/dev/hda1 ro quiet splash noapic nolapic"

---

### Post by adamvert on 2004-11-07
Thanks for the tip, but it hasn't really helped.

My latest theory is that it's due to overheating - according to /proc/acpi/thermal_zone/THRM/temperature, I'm getting up to 66C, which seems unfeasibly high to me :shock: 

Is there a way I can make the CPU fan start up more frequently?

Toshiba Satellite M30 Centrino...

thanks,
Adam

---

### Post by adamvert on 2004-11-10
OK, fixed it... it looks like the problem was with my memory.  I removed one of the memory sticks (I had 1x256, 1x512, removed the 256), and now everything's just fine.

thanks,
Adam

---

