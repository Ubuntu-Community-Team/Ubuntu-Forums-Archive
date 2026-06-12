---
title: "Link two unallocated partitions"
date: 2014-07-21
forum: General Help
---

### Post by Alessandro_Gessa on 2014-07-21
Hello everyone,

I want to link two unallocated partitions from gparted.
One was an ext4 partition where i had my files and the other a NTFS partition where i had Windows Operative System.
I want to link them and reinstall windows again, so i can dual boot ubuntu and windows (i've already another partition with ubuntu installed)
What can i do? I already have gparted installed and an USB Flash Drive with gparted live installed.

Thank you

---

### Post by oldfred on 2014-07-21
Windows will only install to a primary partition formatted NTFS with the boot flag.

If partitions/unallocated space are not adjacent, then you have to move existing partitions around so the unallocated is together. That always has some risk so very good backups are required.

May be best to attach screen shot from gparted. In advanced editor you can easily attach anything using the paperclip icon. Do not post in line as not everyone has high speed Internet and it can lock up system for a while.

---

