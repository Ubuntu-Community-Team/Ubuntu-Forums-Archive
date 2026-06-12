---
title: "Is &quot;C:\wubi&quot; required instead of &quot;C:\Wubi&quot;?"
date: 2007-07-16
forum: General Help
---

### Post by Xenomorph on 2007-07-16
Silly question, I noticed "\wubi" was not capitalized on my C:\, making it stand out from EVERY other folder and file.
 

When capitalized to "\Wubi", it makes Linux unbootable.

Is there something I could change to make Linux look for "\Wubi" instead of "\wubi" ?

(yeah, i know, weird question. i cant be the ONLY person who doesnt like the lowercase name).

---

### Post by ago on 2007-07-16
you'd better get used to lower case :D
but anyway, if you change the case, you need to change c:\wubi\boot\grub\menu.lst

---

### Post by Xenomorph on 2007-07-16
i can handle lowercase just fine.

however, it just really stood out on my C: drive in Windows.

i'm in Ubuntu right now (C:\Wubi).

i just got my TV card working (installed tvtime, had to add "bttv card=3 tuner=6" to /modprobe.d/options).

---

### Post by fluteflute on 2007-07-18
Linux is case sensetive - WIndows isn't.

---

### Post by Xenomorph on 2007-07-20
It seems like changing "\wubi" to ANYTHING else causes boot issues.

If it is left as /wubi/, menu.lst is regenerated every boot with the correct path.

If it is changed to something else, menu.lst is regenerated without the correct path.

I always have to pick the non-generated entry on menu.lst (the last one). It doesn't matter if I update the entries in menu.lst with the correct paths,on each reboot the paths are stripped out, preventing it from booting up then (again, unless I choose the last menu.lst entry).

What program or script is used to update menu.lst on every boot? Where is it located? Where does it get its settings from?

---

### Post by Xenomorph on 2007-07-20
Here's an example of changing the installed location.

If left at the default (C:\wubi), it looks like menu.lst stays with this:

kernel		/wubi/boot/vmlinuz-2.6.20-16-generic root=/dev/hda1 ro quiet splash

(which works)

But when changed to ANYTHING else, menu.list gets auto updated with this:

kernel		/boot/vmlinuz-2.6.20-16-generic root=/dev/hda1 ro quiet splash

or this:

kernel		/vmlinuz-2.6.20-16-generic root=/dev/hda1 ro quiet splash

which results in a "File not found" error on boot.


edit:

manually running "update-grub" again changes the line to this:

kernel		/boot/vmlinuz-2.6.20-16-generic root=/dev/hda1 ro quiet splash

regardless of where the "vmlinuz-2.6.20-16-generic" is actually located. where is it getting the path information from????

---

