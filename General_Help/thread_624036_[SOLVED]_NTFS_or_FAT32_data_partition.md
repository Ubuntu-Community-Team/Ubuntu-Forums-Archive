---
title: "[SOLVED] NTFS or FAT32 data partition?"
date: 2007-11-26
forum: General Help
---

### Post by drfox on 2007-11-26
Now that NTFS is supported, does it make more sense to format a /data partition shared between Windows and Linux as NTFS or FAT32?

Thanks

Larry

---

### Post by rsambuca on 2007-11-26
Definitely not FAT32.  It is a terribly antiquated filesystem that is prone to problems and requires consistent maintenance.  If you use Windows more than linux, than use ntfs.  If you use Linux more, then use ext3 with the fs-driver for windows.

---

### Post by drfox on 2007-11-26
Actually, I've bought a new computer for my son and his family for Xmas. It came with Vista, but I'm trying to get their kids to use linux, like they do on my machine here at home when we babysit. I'm just partitioning it now, and I'll set up the /data partition as ext3. Thanks very much for the speedy reply. 

Larry

---

### Post by rsambuca on 2007-11-26
> **drfox said:**
> Actually, I've bought a new computer for my son and his family for Xmas. It came with Vista, but I'm trying to get their kids to use linux, like they do on my machine here at home when we babysit. I'm just partitioning it now, and I'll set up the /data partition as ext3. Thanks very much for the speedy reply. 

Larry

If you are using Vista, just make sure you use the "XP compatibility mode" when installing the driver.

---

### Post by drfox on 2007-11-26
Grazie!  

Larry

---

