---
title: "Fat?"
date: 2007-06-10
forum: General Help
---

### Post by jgrabham on 2007-06-10
What file system should I use for a 2nd HDD which will be used both in winxp and ubuntu?  I'd say FAT32, but the 4gb file limit?  Will it affect me ripping DVDs to my HDD

---

### Post by hysteresis on 2007-06-10
Why don't you use ext2 along with the windows ext2 file reader at  [http://www.fs-driver.org/](http://www.fs-driver.org/) ?

---

### Post by jgrabham on 2007-06-10
> **hysteresis said:**
> Why don't you use ext2 along with the windows ext2 file reader at  [http://www.fs-driver.org/](http://www.fs-driver.org/) ?

It sounds as if its going to be slow!

---

### Post by gerscht on 2007-06-10
DVD ripping shouldn't be a problem as all programs I know split files after 2GB (I think it's 2GB filesize limit, not 4GB as you have written)...
You can also rip them to your primary harddrive (which I suppose is ext3), and convert it from there, so you won't get a problem with file sizes

---

### Post by Zootropo on 2007-06-10
I'd say FAT32, even with the file size limite.

You could use NTFS, as NTFS-3G seems to be very stable and reliable, but NTFS is a closed format, so you'll never be sure.

---

