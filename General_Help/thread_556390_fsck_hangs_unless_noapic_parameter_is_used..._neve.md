---
title: "fsck hangs unless noapic parameter is used... never heard of this before"
date: 2007-09-21
forum: General Help
---

### Post by Keyper7 on 2007-09-21
I mentioned this in a recent thread concerning a different problem, but since the two problems might
have nothing in common, I'll repeat myself here:

My problem is: unless the noapic kernel parameter is given, the fsck disk check hangs at a random
percentage. It usually hangs between 70% and 80%, but sometimes after that and once it froze before
30%. I've read a lot in this forum about hangings when noapic is not given, but this is the
first time I face this happening specifically with fsck.

I'm running Feisty amd64 in a HP Pavilion DV6258se. Fsck works fine if I use noapic and the system
works perfectly if fsck is not called (even without noapic).

Thanks.

---

### Post by dcstar on 2007-09-21
> **Keyper7 said:**
> I mentioned this in a recent thread concerning a different problem, but since the two problems might
have nothing in common, I'll repeat myself here:

My problem is: unless the noapic kernel parameter is given, the fsck disk check hangs at a random
percentage. It usually hangs between 70% and 80%, but sometimes after that and once it froze before
30%. I've read a lot in this forum about hangings when noapic is not given, but this is the
first time I face this happening specifically with fsck.

I'm running Feisty amd64 in a HP Pavilion DV6258se. Fsck works fine if I use noapic and the system
works perfectly if fsck is not called (even without noapic).

Thanks.

If you don't have a dual-core CPU (or multiple CPUs), then you can use the noapic parameter without any negative issues.

I have seen various Linux issues with multiple CPU motherboards only running a single (core) CPU, which go away with a noapic.

---

### Post by Keyper7 on 2007-09-22
Noapic unfortunately is not an acceptable solution for me so far, as using it makes the ehci_hcd
module throw a lot of spurious interrupts, making one of the cores completely occupied.

---

### Post by GLRenderer on 2007-10-01
I can confirm that this issue is true. I have an HP6338se with dual boot. I have the same resulting effects of fsck freezing at random completion stages.
This means that I had to modify the /boot/grub/menu.lst every single time that the kernel is updated.

---

### Post by Keyper7 on 2007-10-05
> **GLRenderer said:**
> I can confirm that this issue is true. I have an HP6338se with dual boot. I have the same resulting effects of fsck freezing at random completion stages.
This means that I had to modify the /boot/grub/menu.lst every single time that the kernel is updated.

I think I didn't understand... Why do you have to change the menu.lst file because of the fsck freezing?

---

### Post by dcstar on 2007-10-05
> **GLRenderer said:**
> I can confirm that this issue is true. I have an HP6338se with dual boot. I have the same resulting effects of fsck freezing at random completion stages.
This means that I had to modify the /boot/grub/menu.lst every single time that the kernel is updated.

If you mean that you manually have to add the "noapic" back in, you can easily modify your menu.lst file to do that automatically after an update, just do a search for instructions.

---

