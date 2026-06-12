---
title: "internal NTFS drive read_write permission suddenly denied"
date: 2018-06-23
forum: General Help
---

### Post by carusoswi on 2018-06-23
I have been using my second hard drive formatted as NTFS for years.  Suddenly, the folders and files are set to read only.  I have tried to change them, but the changes do not hold.  What could be wrong, and how can I fix this?

Thanks for your help.

Caruso

---

### Post by yancek on 2018-06-23
That generally means a filesystem error and the best way to check and/or try to repair it is to run chkdsk from windows.  You may try ntfsfix on the various partitions on the drive from Ubuntu but, unless there are very minor problems, you need windows chkdsk because it is a windows filesystem.

---

### Post by carusoswi on 2018-06-23
Thank you for your reply.  I will run chkdsk from windows and see how it goes.
Caruso

---

