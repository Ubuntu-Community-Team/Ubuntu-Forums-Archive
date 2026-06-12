---
title: "Permissions trouble"
date: 2007-06-01
forum: General Help
---

### Post by posiedon321 on 2007-06-01
I am running Feisty Fawn i386 dual-booting with Windows XP. I mount my flash drive and it will read and write with no problem, then suddenly and for no apparent reason it becomes a read-only drive and I can no longer save anything to it. What causes this and how can I prevent it?

---

### Post by Ek0nomik on 2007-06-04
Does root own the device or is it by any chance formatted as NTFS?

If it was formatted as NTFS I have no idea how you were able to write to it earlier.

---

### Post by mkoehler on 2007-06-04
If it was formatted as NTFS, the ntfs-config application should fix read/write problems.

---

### Post by posiedon321 on 2007-06-04
> **Ek0nomik said:**
> Does root own the device or is it by any chance formatted as NTFS?

If it was formatted as NTFS I have no idea how you were able to write to it earlier.

It's formatted FAT. I don't know who owns it. How do I determine that and can ownership be changed?

---

### Post by hellmet on 2007-06-30
I've exactly the same problem here. This has started becoming a frequent feature these days on my comp.

---

