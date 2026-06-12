---
title: "Recovery folder and file?"
date: 2021-08-31
forum: General Help
---

### Post by fairbird on 2021-08-31
I have internal HDD with bad sectors. I was wiped the HDD to fix bad sectors but the HDD Still have problem So I replaced it with new one...
But I have forgotten to backup my Folders/Files before wipe the HDD. Is there any way to recovery the folders and files with same name, By using Ubuntu 21.04 ?!!

---

### Post by TheFu on 2021-08-31
> **fairbird said:**
> I have internal HDD with bad sectors. I was wiped the HDD to fix bad sectors but the HDD Still have problem So I replaced it with new one...
But I have forgotten to backup my Folders/Files before wipe the HDD. Is there any way to recovery the folders and files with same name, By using Ubuntu 21.04 ?!!

No easy way.  There are recovery tools, but they recover files with a sequential name, many versions, so there could be 50 versions of the same file with only your eyes able to tell the difference.  Google "Ubuntu Data Recovery" to learn more about those tools.  Plus, it would be smart to **clone** the drive that you hope to restore BEFORE doing anything else. To clone a drive is very different from creating a backup. They are very different purposes.  For the specific use you've described, use **ddrescue** and hope the HDD doesn't completely die during the clone effort.

On Unix, there are these things called "backups."  We make those BEFORE anything bad happens, so we can survive logical and hardware issues.  Restoring backups is relatively simple if just data files are included, but if no backup was made BEFORE it is needed, sorry. No much anyone can due.

Versioned backups are pretty easy to make for a single-user system.  [Https://ubuntuforums.org/showthread.php?t=2465035&p=14049979#post14049979](Https://ubuntuforums.org/showthread.php?t=2465035&p=14049979#post14049979) has a few examples for backups.

---

### Post by fairbird on 2021-09-01
I will try with TestDisk tools later ..
Thank you

---

