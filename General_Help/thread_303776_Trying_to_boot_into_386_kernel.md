---
title: "Trying to boot into 386 kernel"
date: 2006-11-20
forum: General Help
---

### Post by TurkVU on 2006-11-20
I'm trying to boot into the 386 kernel from the grub menu because i've heard it might solve my graphics performance issues and after I select the 386 entry from the menu, I get this message:

Starting up...
Uncompressing Linux...Ok, booting the kernel.
..MP-BIOS bug: 8254 timer not connected to IO-APIC
Kernel panic: VFS: Unable to mount root fs on 00:00


What does that mean? Kernel panic doesn't sound good :)

---

### Post by TurkVU on 2006-11-20
My menu.lst file in grub looks fine - this is the entry for the 386 kernel:

title		Ubuntu, kernel 2.4.27-2-386
root		(hd0,0)
kernel		/boot/vmlinuz-2.4.27-2-386 root=/dev/hdb1 ro quiet splash
initrd		/boot/initrd.img-2.4.27-2-386
quiet
savedefault
boot

---

### Post by TurkVU on 2006-11-20
nm -- didn't have the kernel completely installed from synaptic.

---

