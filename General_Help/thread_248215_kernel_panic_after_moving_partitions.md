---
title: "kernel panic after moving partitions"
date: 2006-08-31
forum: General Help
---

### Post by Burke on 2006-08-31
I just made the following changes to my system:
Shrank Root FS
deleted swap
made extended partition
created swap in extended partition
copied root to extended

/boot is ext2 and root is reiser.

I changed /boot/grub/menu.lst... I updated the "root=" part to reflect the new partitions... I have an entry for the old root partition and one for the new root partition.  

Problem is, when I try to boot either of them, I get a kernel panic. here's the error:

...
savedefault
boot
Uncompressing Linux... Ok, booting the kernel.
[17179575.888000] Kernel panic - not syncing: I/0 error reading memory image
[17179575.888000]


...and that's all I get . I went into /etc/fstab and updated the swap and root locations there too. I don't know what else to do. It seems like it should work, but it doesn't.

Does anyone have any clue what's going on?

Thank you so much for your help.



EDIT: I disabled quiet, and here's the relevant part:

Begin: Running /scripts/local-premount ...
[17179575.548000] Attempting manual resume
[17179575.548000] attempt to access beyond end of device
[17179575.548000] hda3: rw=16, want=8, limit=2
[17179575.548000] Kernel panic - not syncing: I/O error reading memory image


hda3 used to be my swap partition, but now it's an extended partition.

What the heck....

---

### Post by Burke on 2006-08-31
I GOT IT!

I gunzipped all my initrds, opened them in a hex editor, replaced hda3 with hda5, and recompressed. It boots!

---

