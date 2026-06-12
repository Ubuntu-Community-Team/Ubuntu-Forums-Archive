---
title: "After upgrade to 7.10 (Gutsy), booting 2.6.22-14-generic hangs"
date: 2007-11-02
forum: General Help
---

### Post by leifw on 2007-11-02
I had a very function 7.04 installation.  After upgrading to 7.10, I can't boot into the 2.6.22-14-generic kernel.  After hitting Alt-F1, it looks like it's hanging around the time that it accesses /dev/sdb.  I have a RAID1 setup with my root partition on /dev/md0.  Thankfully, the non-generic 2.6.22-14 kernel will start, but I'd really like to run on the generic kernel because I have a dual core processor.  

Do you have any suggestions?  I'd be happy to provide more information.

Thanks,

Leif

---

### Post by dcstar on 2007-11-02
> **leifw said:**
> I had a very function 7.04 installation.  After upgrading to 7.10, I can't boot into the 2.6.22-14-generic kernel.  After hitting Alt-F1, it looks like it's hanging around the time that it accesses /dev/sdb.  I have a RAID1 setup with my root partition on /dev/md0.  Thankfully, the non-generic 2.6.22-14 kernel will start, but I'd really like to run on the generic kernel because I have a dual core processor.  

Do you have any suggestions?  I'd be happy to provide more information.

Thanks,

Leif

You can try booting with the "noapic" boot string option (put is at the end), that may get it going without dual processor support.

---

### Post by Slade Winstone on 2007-11-02
Hi,

I have had a really similar problem. I'm running an ASUS A8M Laptop with Gutsy and 2.6.22-14-generic would freeze on boot and lockup without any errors that I could find, but 2.6.20-16-generic would boot fine.

I edited the kernel options in /boot/grub/menu.lst and added:

acpi=off

and now everything starts fine.

Not sure if this helps particularly with the dual core processor.

Best of luck with it all.

Slade.

---

### Post by leifw on 2007-11-03
I tried both the "noacpi" and the "acpi=off" suggestions.  Neither one seemed to have any effect.
Thanks for the suggestions.

Do you have any other ideas?

---

### Post by Slade Winstone on 2007-11-04
Nope, sorry.  

It looks like their are a lot of problems with the 2.6.22-14-generic kernel.

Hope you can sort it out.

Slade.

---

### Post by leifw on 2007-12-26
It's all better after 2.6.22-14 showed up.

---

### Post by Slade Winstone on 2008-01-05
Hi,  just a quick update:

2.6.22.14 Kernel set nosmp noapic

UPDATE I have now found kernel boot parameters that will allow ACPI to run. Instead of setting acpi=off to disable all ACPI (which previously was the only way of booting my A8M), I now use nosmp and noapic which allows some ACPI functionality and a good boot

Add to the end of defoptions and the end of the current kernel in /boot/grub/menu.lst

nosmp noapic

---

