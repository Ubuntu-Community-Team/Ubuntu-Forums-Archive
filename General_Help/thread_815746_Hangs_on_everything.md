---
title: "Hangs on everything"
date: 2008-06-01
forum: General Help
---

### Post by themostunoriginalname on 2008-06-01
Boot into Ubuntu: fails
Boot into Ubuntu recovery mode: Hangs for like... 10 minutes on ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 22 (level, low) -> IRQ 21 and then fails. After that, fsck 1.40.8 runs on /dev/sdb3 and sees that it's clean. fsck runs again, but hangs there.
Boot into Ubuntu LiveCD, but hangs after loading.

Ironically, XP runs without issues.

Any clue how I can fix this?

I have a Gigabyte DS3 if the BIOS is a possible issue

---

### Post by SirPerigrin on 2008-06-01
try booting with acpi=force appended to your kernel

---

### Post by themostunoriginalname on 2008-06-01
How do I do that?

And update:

I took off my second hard drive and it's booting.

---

### Post by themostunoriginalname on 2008-06-01
I put back in my second drive and it hangs again

---

### Post by SirPerigrin on 2008-06-01
drop to command line during bootup from grub to add the lines to the boot, or if you can get in now, edit /boot/grub/menu.lst and add the lines to your kernel there. If your unsure exactly where to put it post the file contents here and ill help you out.

Also recomend checking the jumpers on BOTH drives, the 1st drive may have different settings when Primary w/ slave and when Solo w/o slave

---

### Post by themostunoriginalname on 2008-06-01
Still hangs with both drives.

---

### Post by themostunoriginalname on 2008-06-02
does anyone else have a suggestion?

---

