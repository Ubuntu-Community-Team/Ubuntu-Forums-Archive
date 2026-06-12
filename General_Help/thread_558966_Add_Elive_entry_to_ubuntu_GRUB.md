---
title: "Add Elive entry to ubuntu GRUB"
date: 2007-09-24
forum: General Help
---

### Post by le1 on 2007-09-24
I'm an absolute beginner, so please try to give me a simple answer.

Few days ago I installed Elive gem linux on my computer and (since i don't know much about GRUB and my ubuntu works like a dream) during the installation I've chosen "do not install GRUB (elive won't boot)" option.
Now my question is: how can I go about with adding entry to ubuntu GRUB to make Elive start (I loved the way dreamlinux worked that issue out, you have an option to add entry to existing GRUB, and it works beautifully).

Any advices will be appreciated. Thanks geeks.

---

### Post by dabl on 2007-09-24
Basically, you need to add the Elive boot information below the "End Debian Automagic Kernels List" line in your /boot/grub/menu.lst file, using the same notational style as you observe for the Ubuntu boot lines, but referring to the partition and kernel name/number for the Elive kernel.


Here's a good place to start your studies on the subject:

[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

:)

---

### Post by le1 on 2007-09-24
ok so here is what I have:

title		Ubuntu
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=1...3a-0c..-4...-b5fa-c...ce... ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
savedefault

this is what dreamlinux added (automatically):

title	dreamlinux
kernel	(hd0,1)/boot/vmlinuz-2.6.18.1-kanotix-1 root=/dev/sda2 ro quiet vga=791 splash=silent
initrd	(hd0,1)/boot/initrd

I see (& I repeat I am pretty pretty ungeekable) little similarities:

BTW Elive will run from the same partition as dreamlinux I replaced it with elive.

But what about :
quiet ?
savedefault ?
ro quiet ?
vga ?
splash=silent ?
initrd ?

What is this and how should I go about with it ?

---

### Post by logos34 on 2007-09-24
> But what about :
quiet ?
savedefault ?
ro quiet ?
vga ?
splash=silent ?
initrd ?

What is this and how should I go about with it ?

more about options here:
[http://users.bigpond.net.au/hermanzone/p15.htm#defoptions](http://users.bigpond.net.au/hermanzone/p15.htm#defoptions)

Look in the elive /boot for the vmlinuz and initrd (kernel and initial ramdisk image) and paste them into menu.lst, either using the above format (as for dreamlinux) or ubuntu's.  Try a simple entry like this with just 'ro' option:

title elive
root (hd0,1)
kernel /boot/vmlinuz... root=/dev/sda2 ro 
initrd /boot/initrd...

If the X server gives you a problem, then add the vga option back

---

### Post by le1 on 2007-09-24
there it is:

title	Elive (or whatever)
root    (hd0,1)
kernel	/boot/vmlinuz-2.6.18-elive root=/dev/sda2 ro
initrd	/boot/initrd.img-2.6.18-elive
savedefault

of course you gotta figure out where is your linux at and type adequate entries.

Elive is pretty good but UbUnTu is the BEST !

---

