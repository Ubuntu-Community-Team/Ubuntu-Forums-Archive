---
title: "[SOLVED] What's a good &amp;quot;Check Laptop After Having Been Dropped&amp;quot; procedure?"
date: 2008-01-04
forum: General Help
---

### Post by Sporkman on 2008-01-04
My wife just called me & told me our active little infant had pulled my laptop off the couch & on to the floor. As always, it was powered on & not in any sleep or suspend type of mode.

When I get home from work & check the thing, is it enough to just see if it appears to be still working properly, or is there other due diligence I'd want to do to detect problems early?

---

### Post by tgalati4 on 2008-01-04
Grab a USB flash drive and transfer your important data.  The next step is supposed to be non-destructive, but if the disk surface or heads are damaged, who knows what will happen?

In a terminal:

>sudo fsck -cc /dev/sda

This will check for bad blocks on the disk.  Could take a while.  Also, check that you can read a CD/DVD.  The optical drives tend to lose alignment after a hard jolt.

Sometimes the RAM needs reseating.

With the laptop powered off, remove the battery and check for contact damage.

---

### Post by Sporkman on 2008-01-04
> **tgalati4 said:**
> In a terminal:

>sudo fsck -cc /dev/sda

This will check for bad blocks on the disk.  Could take a while.  Also, check that you can read a CD/DVD.  The optical drives tend to lose alignment after a hard jolt.

Sometimes the RAM needs reseating.

Thanks, I'll check those.

---

### Post by nick_h on 2008-01-04
> Sometimes the RAM needs reseating.

It might be worth running memtest86+ from the grub boot screen.

---

