---
title: "how to use unionfs for root"
date: 2008-06-21
forum: General Help
---

### Post by framallo on 2008-06-21
hey,
i'm looking to use a SD card reader in order to spindown the HD from the laptop.
The idea is to boot from HD, then create a unionfs between the SD and HD.

Planning for a second version: /home in a third partition in HD,  use aufs, squashfs and encryption.

my fstab looks like this:

UUID=blah /mnt/hd ext3    defaults,errors=remout-ro  0 1
UUID=blah /mnt/sd ext3    defaults,errors=remout-ro  0 0
unionfs   /       unionfs dirs=/mnt/sd=rw:/mnt/hd=rw 0 0

i have some read-only errors, and X doesn't load.
Can't find a good howto about unionfs with /
the unionfs syntax is correct on fstab? is like mount isn't?

any ideas?

thanks

---

