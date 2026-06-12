---
title: "Can't boot computer with XP CD after i install ubuntu"
date: 2007-08-22
forum: General Help
---

### Post by Afshin_zavar on 2007-08-22
Hi all mates

Can't see the blue screen of Windows XP when i try to boot computer, after i install Ubuntu...:(

---

### Post by glotz on 2007-08-23
When the computer boots, you should see a menu containing ubuntu (with different kernels) and windows. Do you see it?

---

### Post by Afshin_zavar on 2007-08-23
> **glotz said:**
> When the computer boots, you should see a menu containing ubuntu (with different kernels) and windows. Do you see it?
Yes I do. But I've Uninstalled Grub (using SuperGrub recovery CD) and still can't boot computer with windows xp bootable CD to install a fresh Windows.:(

---

### Post by glotz on 2007-08-23
I once took a look at the super grub CD and found it ...confusing.

When you boot the box, open the BIOS setup (usually press del or F1 or maybe some other key that reads onscreen) and make sure you're booting off the CD. That should do it.

---

### Post by Afshin_zavar on 2007-08-23
Hi
> **glotz said:**
> 
make sure you're booting off the CD. That should do it.
I've already done this. 

Just I can't see the **blue screen** of WindowsXP when it tries to boot itself from the CD ( it hangs...)

---

### Post by merlinus on 2007-08-23
Is it possible that the cd has defects or has gotten scratched?  Does it work on another cd drive or computer?

-merlin

---

### Post by aldenhg on 2007-08-23
I've seen the XP install CD hang before and it's usually been because of bad RAM. Had you not deleted GRUB you could easily do this, but instead you'll have to download the memtest86 iso from [here]("http://www.memtest.org/download/1.70/memtest86+-1.70.iso.zip"), burn it to a cd and boot from it. Let it run it's course and if you get no errors, it's probably the XP install CD itself. Another XP CD can be had from various outlets, most of them being in a gray legal area and therefore not linkable from here - though I'm sure you get my drift.

---

