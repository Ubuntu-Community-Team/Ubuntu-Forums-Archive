---
title: "GParted Abilities"
date: 2008-04-23
forum: General Help
---

### Post by Yuki_Nagato on 2008-04-23
Is GParted able to merely resize my partitions?  I do want them deleted and reformated, but merely resized.  If it does, is it isolated to Linux (ext3) partitions, or will it work for the Windows brand as well?

---

### Post by odin1965 on 2008-04-23
Yes, Gparted can resize NTFS partitions, which is what windows uses. It used to be a good idea to defrag them 1st in Windows, but that is no longer required. I still do it though, just paranoid :).

If you resize the partition Windows is installed on it will force a disk check next time you boot into windows. Don't worry, this is normal.

---

### Post by odin1965 on 2008-04-23
Oh, one other thing. you should leave the start of the windows partition where it is, as the first partition on the disk and shrink it from the end. Windows sometimes doesn't like it any other way.

---

### Post by Tim Sharitt on 2008-04-23
I'm sure you already know this, but I'll add it anyway. Be sure to back up everything if possible, not just the partitions you are resizing. I found out the hard way that when something goes wrong with gparted, it can be very bad.

---

### Post by Yuki_Nagato on 2008-04-23
The partition side to chip from is an excellent point.

Thank you both.

---

