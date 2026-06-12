---
title: "Reformatting HOME partition to NTFS"
date: 2014-01-29
forum: General Help
---

### Post by jp734 on 2014-01-29
I have a **/home** partition right now formatted as ext3. I am thinking about reformatting it to NTFS so when I boot the pc to Windows7 I can read my files.

Steps I'm thinking about doing:
1. Backup all files
2. Format partition to NTFS
3. Restore all files

sda4 is my /home partition and since I'm just reformatting it, it will remain as sda4. /home

Will this create a problem for me?

---

### Post by carl4926 on 2014-01-29
Yes it's a problem
You should not use windows file systems in Linux - at least not as part of the system.

---

### Post by SeijiSensei on 2014-01-29
NTFS does not support the same filesystem characteristics like permissions that Unix-styled filesystems like ext4 do.  You cannot use an NTFS filesystem as /home.

What you can do is partition the drive and create a separate, NTFS-formatted partition that you can share between the operating systems.  Or else write everything from both OS's to shared network locations.

---

### Post by jp734 on 2014-01-29
Thanks...Glad I asked before doing it :-)

---

### Post by jp734 on 2014-01-29
Marked as solved. Will just use a separate partition to share as SeijiSensei suggested.

---

