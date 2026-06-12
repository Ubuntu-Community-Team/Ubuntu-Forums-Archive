---
title: "Best file system for backup storage?"
date: 2013-03-08
forum: General Help
---

### Post by nickdc on 2013-03-08
I've looked at dozens of tutorials and help pages for various bits of software, and done a fair bit of googling, but nowhere can I find any recommendation as to the best file system to have on an external drive being used to back up to. In my case I want to store cloned images (using Redo most probably) of both Windows and Ubuntu partitions. The drive I intend to use is formatted to NTFS and has old "Ghost" images on it. These are pretty redundant now and could be wiped. Should I bother? Would it be best to reformat to ext3 or 4? Are there advantages or disadvantages either way? (The clone of the Windows partition is "just in case", prior to wiping it. I'm at home with Ubuntu now and beginning the process of parting company with Windows, hopefully forever.)

---

### Post by Cheesemill on 2013-03-08
That all depends on what filesystems your backup software supports.

If you don't need to access the drive from Windows and your backup software supports it then I'd go for ext4.

If you are going to be getting rid of Windows in the future then you should stop using NTFS. A lot of the problems that can arise on an NTFS filesystem can only be fixed by running Windows tools on the drive, if you don't have Windows then you won't be able to fix these issues if they occur.

---

### Post by nickdc on 2013-03-08
Thanks, Cheesemill, that's what I needed to know. I'd half guessed, but it's good to get confirmation from more expert users. Many thanks.

---

