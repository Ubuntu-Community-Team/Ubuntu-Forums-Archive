---
title: "cant copy large file to external hard drive"
date: 2007-08-27
forum: General Help
---

### Post by anon999 on 2007-08-27
when i try to copy a 7.7gb file to my external hard drive, it stops at 4.0gb. tried three times, need a solution please. external hard drive is not full.

---

### Post by jocko on 2007-08-27
What filesystem do you have on the external drive? FAT32?
I think the maximum file size for FAT32 is 4Gb.

---

### Post by davidjmayo on 2007-08-27
> I think the maximum file size for FAT32 is 4Gb.
correct

---

### Post by anon999 on 2007-08-27
wow, i'll have to research to find a better format.ting for my drives.

---

### Post by davidjmayo on 2007-08-27
use NTFS (you can convert them from Windows ---see help convert)
*buntu will read NTFS but for write access you need to install ntfs-3g

---

### Post by anon999 on 2007-08-28
> **davidjmayo said:**
> use NTFS (you can convert them from Windows ---see help convert)
*buntu will read NTFS but for write access you need to install ntfs-3g

it seems something so fundamentally important would come built into ubuntu, is this a legal problem a la the mp3 codecs or what?

---

### Post by Steveway on 2007-08-28
No it's a problem that the specs for NTFS are not open.
We don't know how it works and everything that we can do has been reverse engineered.
But why not use ext3 as a filesystem? It's far superior to NTFS.

---

### Post by Wolki on 2007-08-28
> **anon999 said:**
> it seems something so fundamentally important would come built into ubuntu, is this a legal problem a la the mp3 codecs or what?

It's rather new and still was beta until recently.

---

### Post by b0ng0 on 2007-08-28
Format it using ext3. NTFS is only usable in Windows really (I don't think OSX can even read/write to it). ext3 is more universal (although copying from NTFS to ext3 is painfully slow).

---

### Post by anon999 on 2007-08-28
i plan on dual booting with my new computer via grub using ubuntu and probably vista (although if i can find out how to work a pirated version of XP, that sould be preferred, PMs please on that topic), would ext3 be a problem?

---

### Post by notwen on 2007-08-28
If you're looking for a solution other than formatting your drive.  You could always use a RAR-like archiver to transfer the file over and then un-archvie it once it gets to the place it needs to be. =]

---

