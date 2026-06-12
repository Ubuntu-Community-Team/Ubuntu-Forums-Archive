---
title: "Why Is My Ubuntu Pretending to be Case-Insensitive?"
date: 2019-10-09
forum: General Help
---

### Post by rebeltaz on 2019-10-09
Before... a folder called [Special] could be renamed [special]. Now, if I try to do that with rename or kbrename or even from within nemo, it tells me that a folder called that already exists. Is there something I can change to fix this?

What I've been doing is renaming the folder [SSPecials] first and then renaming it [specials] but that is a pain in the...

---

### Post by Impavidus on 2019-10-10
Ubuntu (as ever other Unix-type operating system) is case sensitive. So is the ext4 filesystem. NTFS and FAT however are not. Are you by any chance dealing with a directory on an NTFS or FAT filesystem, a.k.a. a filesystem that works on Windows?

---

### Post by rebeltaz on 2019-10-15
Yep. I checked and that partition is NTFS. Thanks.

---

