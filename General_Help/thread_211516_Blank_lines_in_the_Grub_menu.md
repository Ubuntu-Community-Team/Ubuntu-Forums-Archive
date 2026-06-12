---
title: "Blank lines in the Grub menu"
date: 2006-07-08
forum: General Help
---

### Post by xmastree on 2006-07-08
Is it possible?
I'm dual-booting my dad's PC, and have altered the menu.lst so that it reads like this:

Linux
Windows
Other stuff which needn't concern you:
Ubuntu yadda yadda recovery mode
Memtest

(those last two are actually as they were originally, but I can't remember exactly...)

Is it possible to insert a couple of blank lines after the Windows entry, to seperate them more? Dad's almost 80, and I think it would be clearer for him if the two main options were out on their own.

---

### Post by tonyr on 2006-07-08
Here's the best I could do.

```

sudo touch /boot/vmlinuz-dummy
sudo touch /boot/initrd-dummy

```
and add these lines at the target break point in **menu.lst**:
```

title		-
root		(hd0,6)
kernel		/boot/vmlinuz-dummy
initrd		/boot/initrd.img-dummy
boot

title		*
root		(hd0,6)
kernel		/boot/vmlinuz-dummy
initrd		/boot/initrd.img-dummy
boot

```
Use your own (hdN,M).

This is, of course, fooling **grub**.  It does not like blank
**titles**, apparently, and **titles** have to be unique, and sections
have to be "well defined".  It doesn't seem to care whether the files
you name are legal, only that they exist.  You could experiment with 
non-printable characters in the titles, I guess.

Selection of one of those lines in the displayed menu results in an
error message, "press ENTER to continue", and a return to the menu.

---

### Post by xmastree on 2006-07-09
Hmmm... that's messy.
I think I'll just leave it as it is, he seems to be getting used to it.

---

