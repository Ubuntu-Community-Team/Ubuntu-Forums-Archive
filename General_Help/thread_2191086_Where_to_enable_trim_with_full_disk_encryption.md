---
title: "Where to enable trim with full disk encryption?"
date: 2013-11-30
forum: General Help
---

### Post by PaulBx on 2013-11-30
Hi all. I have 13.04 (I think!) using kernel 3.8.0-33. I have full disk encryption and I suppose LVM too since the lubuntu installer always combines the two. I use the newer Grub and the system uses UEFI boot. Actually it's not really full disk encryption as my boot partitions are of course not encrypted. Only sda3 is.

From my reading it appears there are 3, maybe 4 possible places to invoke trim:

1) "discard" in the mount line in /etc/fstab
2) "discard" in /etc/crypttab
3) "allow-discards root_trim=yes" in the etc/default/grub file at the line GRUB_CMDLINE_LINUX
4) old grub used to have a place in menu.lst but this may be obsolete.

I'm just wondering if using #1 by itself is good enough, or if I have to also invoke it in other places. I have dug around here looking for info and it isn't entirely clear.

Oh, BTW when I query I get this:
```

$ sudo hdparm -I /dev/sda | grep "TRIM supported"
       *    Data Set Management TRIM supported (limit 16 blocks)

```

---

### Post by PaulBx on 2013-12-03
Bump.

I did find [this page](http://blog.patshead.com/2012/12/whole-disk-encryption-with-an-ssd.html), which suggested, "If you want to enable TRIM support, you will need to make sure it is enabled in both your /etc/inittab file AND your /etc/crypttab file."

Well I don't have /etc/inittab, but I did the edit in /etc/crypttab and will boot and see if that works. Wish me luck...

Still not sure how many places I need to enable it.

---

