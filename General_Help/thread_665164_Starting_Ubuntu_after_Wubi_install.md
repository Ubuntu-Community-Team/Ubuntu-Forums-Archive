---
title: "Starting Ubuntu after Wubi install"
date: 2008-01-11
forum: General Help
---

### Post by Kinda Sorta on 2008-01-11
The installation went fine. But after reboot & selecting Ubuntu, I got an error like this

253:1 linear invalid argument count (or something like that-might have been 235)

Is this a disk error?

Setup: Sony VGC RC210G, 1 gig ram, 320 gig HD (raid 0)

---

### Post by ago on 2008-01-12
I'll need the exact error

---

### Post by AndyM3 on 2008-07-21
I've got exactly the same computer and I know that the RAID won't work with Linux. Wubi has its filesystem in a single file (most likely mounted as loop, I didn't try it), but a kernel is used to mount that file. And the kernel doesn't work with the computer's RAID. Sorry.

---

### Post by ago on 2008-07-21
Confirmed, I missed the raid 0 in the original poster. That is not supported by Ubuntu at the moment (fake raid). Either you install on a different drive or you wait for 8.10.

---

### Post by AndyM3 on 2008-07-22
Is there any kernel/patch/OS/driver that supports that kind of RAID? And is it possible for the BIOS to see the two physical drives as one single volume?

---

### Post by ago on 2008-07-22
Yes dmraid is the module you want, but it does not ship in the LiveCD by default, add it manually (it is in the universe repository), while possible, is fairly complex.

---

### Post by AndyM3 on 2008-07-28
Is it possible to actually install Ubuntu via Wubi or natively to a RAID volume?

---

### Post by minhmeoke on 2008-07-29
Wubi, and probably ubuntu itself will not work with software (fake) RAID. If you have a hardware raid controller, then a full install to dedicated partition might work. Look up the raid controller model, and see if there are any suitable drivers for it, you might have some luck with the alternate iso, since it has more drivers than the desktop iso.

---

