---
title: "gparted boot flags - what do they mean?"
date: 2007-02-27
forum: General Help
---

### Post by kliver on 2007-02-27
hi,

i've been resizing (growing) my ext3 partition, where ubuntu is installed.
ext 3 was on hda5 (logical), swap on hda6 (logical), the primary extended is hda4
i took the unused space, copied hda5 to that (new partition name hda7).
worked well.
i then deleted hda5 and hda6, so that hda7 would become hda5. i created a new swap partition which became hda6 again.

all worked well.
i did this, as i knew grub would boot hda5.

everything works, but when i look at gparted, my windows ntfs partition (hda2) has the flag "boot" and my old hda5 had a boot flag as well. my new hda5 doesn't have that boot flag.

all worked well, as i mentioned, but i'm just wondering if i'll be running into some kind of problem in the future as hda5 doesn't have a boot flag in gparted.

what do you guys think?
and where would i set that boog flag?

---

### Post by laidback on 2007-02-27
I've only noticed the boot flag on partitions that boot. I once created a disc that didn't have a boot flag set, it wouldn't boot.
I've never read any info on this so am only going by what I have deduced.

---

