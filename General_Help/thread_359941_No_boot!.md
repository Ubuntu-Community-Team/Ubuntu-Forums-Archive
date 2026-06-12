---
title: "No boot!"
date: 2007-02-12
forum: General Help
---

### Post by beatz on 2007-02-12
Hi there!

I recently installed a sata-hd and moved the kubuntu edgy eft partition to it, after adding serial ata support to the kernel. I actually just copied the whole drive with dd since my old ide and the new sata have the same size, sector, cylinders etc. After changing the grub boot line from root=/dev/hda7 to root=/dev/sda7 everything was working fine.

But now Kubuntu just refuses to boot! It hangs after loading the kernel with something like: Alert! Cannot mount root file system on /dev/sda7

I also noticed that the boot stops for a while trying to access the sata drive. It finds ata1, shows some info, but then themes to be unable to access it.

Also, when I boot the Live-CD it won't show the sata drive. But I am sure it works since I am now doomed to use windows, which is still booting fine.

What's up? The only thing that I might have changed is some update through adept, but I am not sure what packages got updated.

Any help would be appreciated!

---

### Post by beatz on 2007-02-16
Okay, i solved it.

A simple pci=noacpi did the trick. Found it via google. Seems to  be a kernel bug.

Cheers,
Michael

---

### Post by beatz on 2007-02-18
Follow up:

After activating ACPI APIC and ACPI 2.0 support in the bios, it even works without the pci=noacpi kernel command.

That might have been the reason, why it stop working in the first place.

:-\"

---

