---
title: "How can I enlarge my home partition on my new larger cloned drive?"
date: 2023-09-26
forum: General Help
---

### Post by sofasurfer on 2023-09-26
I cloned my 240gb ssd to a new 1tb ssd. But now when I try to resize the home partition using gparted I am unable to. Whats the solution?

---

### Post by sofasurfer on 2023-09-26
Found the problem. The extended partition that contains the individual partitions must be enlarged before you can enlarge the partitions inside of it.

---

### Post by MAFoElffen on 2023-09-27
Dang. So the boot is Legacy, and the Cloned drive is MBR and has a MS-DOS partition table with Extended Logical partitions, because that partition table type is limited at 4 primary partitions.

Recommendation. Since this is still fresh, NOW would be the time, if you wanted too, to convert and setup the replacement disk with a GPT partition tabled disk. GPT partition tables do not have that limitation. Though, it takes adding a boot_bios partition to boot from Legacy BIOS and Grub2 reinstalled.

Do you know if this Machine boots from UEFI? If so, and since converting to GPT would require reinstalling Grub2, that could be converted at the same time.

I know. This is a trivial change to me, which adds great value to how it can be for the future of how the machine is, but the steps doing that can seem daunting to a new user.

Those decisions are yours. But the time to do that would be now... When you have the old drive there as a backup, and the new drive, without much changes done to it yet.

EDIT: You didn't say what type of machine type (Desktop or Laptop), brand and model this was...

---

### Post by TheFu on 2023-09-27
+1 for converting to GPT ASAP. There are many good reasons for this like GPT places the primary and backup partition tables at the "opposite end" of the disk. For linear access drives, that means the most outer and most inner cylinders.  For SSDs, it is likely not really under your control since the placement of any data, including partition tables is 100% virtual designed to minimize writes.

Extended Primary Partitions were a neat hack for a long time, but we haven't needed those since around 2008 in Linux.  Time to move to the 2020s. Use and prefer GPT, if only so you don't lose the flexibility that having 10-100 primary partitions allows.  On one of my systems, I have the equivalent of 30 "partitions" across 8 storage devices, so I suppose, if I were careful, I could fit them all into MSDOS partition tables.  Alas, that isn't how they are setup.  One 500G SSD has 16 partitions and LVs. Logical Volumes can be though of as really smart partitions.  They are handy.

---

### Post by MAFoElffen on 2023-09-28
If that is something you might be interested in--- If you ran the UbuntuForums 'system-info' script and posted the URL of where the report uploads to, then we could come up with a detailed plan on how you could do that.

Right now, we have no idea on what your system "is" and how it is laid out. That support report would fill in the blanks and tell us those needed details. Easier to come up with a recommendation when we know what we are recommending for.

---

