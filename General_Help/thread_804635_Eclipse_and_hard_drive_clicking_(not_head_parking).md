---
title: "Eclipse and hard drive clicking (not head parking)"
date: 2008-05-23
forum: General Help
---

### Post by caldis on 2008-05-23
Hi,

I am running Ubuntu 8.04 on a Samsung laptop.
I have mastered the head parking problem and this does not seem to be related to that.

Whenever I run eclipse I get a constant clicking from the hard drive. About once a second. I have set noatime in fstab. When I close eclipse the clicking stops right away.

Does anyone know where this comes from or how to get rid of this? (Is it possible at all?)

Thank you very much for all answers.

---

### Post by Andruk Tatum on 2008-09-01
I think this is happening because Eclipse is checking any files currently open in eclipse for their last modified date.  If you open a file in eclipse (call it foo.bar), and then execute
```
touch foo.bar
```
Eclipse will realize that the file has been changed on the disk and prompt you to update the currently displayed copy.

Your hard drive must click when a file is read.

That being said, I'm trying to see if there's a way to turn file checking off as I sometimes run eclipse from a flash drive, which have limited read/write operations they can do to any particular section of the flash memory.  I just want my flash drive to last as long as possible.

---

