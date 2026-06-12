---
title: "Installed windows 7 on partition, Ubuntu boot loader disappeared"
date: 2013-04-13
forum: General Help
---

### Post by andy18222 on 2013-04-13
Okay, so I've been using Ubuntu as my main OS with a partition for Linux mint and another spare partition...
Yesterday I decided to install Windows 7 to the spare partition and now, my laptop boots straight into windows 7, with no option to select Ubuntu /mint to boot! I've checked with a live cd and my other 2 partitions are still their, so how can I get the option to boot into Ubuntu back at the system start up? And anyone know why this has happened, so I don't make the same mistake again?

Thanks!

---

### Post by ajgreeny on 2013-04-13
Go to the Grub2-Basics link in my signature and at section 13 you will see how to reinstall grub.  Windows does not see other OSs so simply overwrote grub with its own bootloader.

Alternatively look at boot-repair which can do the same thing, though I have not used it personally.

---

### Post by Mark Phelps on 2013-04-13
> **andy18222 said:**
> ...And anyone know why this has happened, so I don't make the same mistake again?

Thanks!

First of all, it's not a mistake (so don't blame yourself), and second, it's not preventable.  

Any install or reinstall of a Windows OS is going to overwrite the existing MBR and remove  GRUB code previously there.

---

