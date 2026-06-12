---
title: "E/S error, can't delete windows files or wubi ones"
date: 2007-12-01
forum: General Help
---

### Post by 7llusion on 2007-12-01
When I try to delete a windows or wubi file or folder, I get an E/S error, how do I fix this?
PS My Windows broke and I could no longer boot from wubi or boot into windows, so I installed Gutsy on a new partition, so the windows and wubi folders are just a giant waste of space...
Even with root I get this error and E/S might be I/O as I have a french gutsy. ALso I can delete any other files or folders...

---

### Post by SyL on 2007-12-01
I assume this is a NTFS partition. 
This is not possible to write/delete on such partition.

Did you try to simply delete the partition using GParted?

---

### Post by 7llusion on 2007-12-01
I said that I could delete any other folder and file, But I need this partition as it has important data, please help

---

### Post by SyL on 2007-12-01
> **7llusion said:**
> When I try to delete a windows or wubi file or folder, I get an E/S error, how do I fix this? (...)
I said that I could delete any other folder and file, 

are you getting errors when you are trying to delete files from your windows partition?
if so, i guess that this is due to NTFS ... so you will not be able to delete anything from Ubuntu.

> **7llusion said:**
>  But I need this parition as it has important data, please help

But you can read it from Ubuntu!
So just copy what you would like to keep and then delete the partition ...

---

