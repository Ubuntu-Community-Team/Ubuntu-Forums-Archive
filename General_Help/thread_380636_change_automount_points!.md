---
title: "change automount points?!"
date: 2007-03-09
forum: General Help
---

### Post by foormea on 2007-03-09
hi

i was trying to assign two fixed mounting points for my two usb thumbdrives. using uuid or label in fstab didn't work. maybe i just didn't do it the right way but anyway i've tried something else, and even if i could make it work using uuid or label, now i want to understand this "something else" ::) :

first, i made a new rule file for udev that creates 2 symlinks for my 2 different thumbdrives. this works fine:
/dev/stick_mp3 points to the correct node of my mp3 usb stick ; /dev/stick_blue points to the correct node of my blue usb stick

then, i added correct lines in my fstab

problem is, my thumbdrives are still being automounted by HAL the way they were before, ie they're mounted to /media/usbdisk and /media/usbdisk-0. indeed, creating symlinks or fstab entries won't change HAL's policies.
i'm trying to make HAL mount /dev/stick_mp3 to /media/stick_mp3 and to make it mount /dev/stick_blue to /media/stick_blue

i could make exceptions to HAL that would make it not automatically mount these nodes, but i *want* them to be mounted. i just don't want them to be mounted in ugly /media/usbdisk and /media/usbdisk-0

and surprisingly, hal doesn't come with much documentation...

does anyone know how to do that?
thanks

---

### Post by dcstar on 2007-03-11
> **foormea said:**
> hi

i was trying to assign two fixed mounting points for my two usb thumbdrives. using uuid or label in fstab didn't work. maybe i just didn't do it the right way but anyway i've tried something else, and even if i could make it work using uuid or label, now i want to understand this "something else" ::) :
..........

Don't touch etc/fstab for removable drives, the easiest way is to give your removable drive partitions a label, and then Ubuntu will mount them using that label.

I have a USB drive with a EXT3 partition labeled "DCSTAR", and it always mounts in /media/DCSTAR when I plug it in.

Be careful that you use a utility that won't wipe your existing partition data when your label them!

---

