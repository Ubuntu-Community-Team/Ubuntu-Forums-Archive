---
title: "Formatting a write protected sony pendrive"
date: 2013-03-08
forum: General Help
---

### Post by aayus on 2013-03-08
I have this write protected sony pendrive. Due to the write protection, I am unable to copy or delete any data on this pd . How can i format this pd or remove the write protection imposed upon it?:(

---

### Post by Mark Phelps on 2013-03-09
How do you know it's write-protected?

Is it encrypted?

Are you only able to mount it read-only?

If the second, and the filesystem is FAT or NTFS, this means that Linux won't let you mount it because it was not cleanly-removed.

If you stick the Pendrive in an MS Windows PC, it may let you into it -- and then if you safely-remove it, Linux may let you mount it read-write the next time.

---

### Post by aayus on 2013-03-10
It's write protected as when I try to delete the content on it or try to format it, it says read only. Still I am unable to format my pd after sticking it in the Windows and then mounting it on ubuntu.

---

### Post by black veils on 2013-03-10
have you tried the gparted application to create a new partition table, then new partition filling the whole drive? **be careful** to select the usb stick from the top-right selector first. and any action requires the **apply** button.

---

### Post by aayus on 2013-03-10
Tried it, it didn't work.

---

