---
title: "ext3 /boot xfs / boot problem (Grub Error 15)"
date: 2008-03-26
forum: General Help
---

### Post by mvniekerk on 2008-03-26
Hi there
I've got Ubuntu32bit and Vista Business 64bit running happily. One good morning I accidentally booted into my Vista recovery partition (I have an HP laptop).
That reinstalled the Vista bootloader and wiped GRUB

My /boot is on a ext3 partition (sda6) and root is on xfs (sda7).
After this GRUB wipe I've booted the live cd. I've mount sda6 to /boot and run "grub-install /dev/sda"
That reinstalled GRUB but when I try to boot Linux it says "Error 15 File not found"

Any ideas?

---

### Post by justleen on 2008-03-26
the mountpoint / sda names probably have changed. its now looking for the initrd in the wrong place. if you stll get the grub menu, you can press 'e' on the selected option, that will allow you to change the boot options. try some other sda's (sda5, sda7 orso)

of your unsure about all that, try supergrub (works like a charm!)

---

