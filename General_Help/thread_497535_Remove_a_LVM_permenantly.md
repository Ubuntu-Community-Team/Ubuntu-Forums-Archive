---
title: "Remove a LVM permenantly"
date: 2007-07-10
forum: General Help
---

### Post by glave on 2007-07-10
I had a hard drive die on me and I had to remove it from the system to get it to boot again. LVM is now upset that the drive is gone, but I cannot get LVM to remove all of its parts so I can start from scratch.

I have done commands such as:
vgreduce lvm-raid --removemissing
lvremove -f lvm-raid
vgremove lvm-raid

Still yet, if I do something like lvdisplay, I get:
 /dev/mapper/Error|lvm2|lvm-raid|pv1: read failed after 0 of 4096 at 0: Input/output error

How can I completely get rid of this previous lvm setup so I can start over from scratch?

---

