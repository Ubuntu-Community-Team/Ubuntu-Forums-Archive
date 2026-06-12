---
title: "Gutsy won't boot: /sbin/modprobe abnormal exit"
date: 2008-01-17
forum: General Help
---

### Post by MikeBenza on 2008-01-17
Hello all,

I've been having a pretty smooth ride with Gutsy until this morning.  I went to boot it and /sbin/modprobe exits abnormally.  I'm not really sure what to do.  I figured I could try booting an older kernel, but I can't figure out how to do that since GRUB only lists the current kernel.  I'm on the live cd now and I can see there is only one kernel in /boot.

How do I figure out what exactly modprobe is having trouble with?

---

### Post by MikeBenza on 2008-01-17
Here are some screenshots (quite literally).  Keep in mind the third photo begins halfway down the second.  Sorry about the quality.

The *iTCO_wdt: failed....* line and the *intel_rng: FWH...* line too always occur on boot.

---

### Post by MikeBenza on 2008-01-17
...anyone....?

---

### Post by Mintux on 2008-03-07
I have the same problem with the Gutsy live CD. It won't boot in either mode (graphic, non-graphic) it won't even check CD for errors. This means that there's no hope of installing Ubuntu on that box.

The boot process exits with:

udevd_event[2131]: run_program: '/sbin/modprobe' abnormal exit

and dumps me to Busybox.

I have seen several other people having this problem since Gutsy camre out, but no one seems to have any ideas.

If I try to boot without the splash screen, it just stops with some ******** about not being able to access fd0 (the floppy drive). I'm pretty sure my floppy drive has nothing to do with it.

I have seen a lot of people having similar problems with newer SiS ATA-controllers. I do however not think this motherboard is equipped with one of those, as it's pretty old.

---

