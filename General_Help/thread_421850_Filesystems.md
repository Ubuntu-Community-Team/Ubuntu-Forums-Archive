---
title: "Filesystems"
date: 2007-04-24
forum: General Help
---

### Post by Harkainos on 2007-04-24
I will most likely be wiping my hd clean and reinstalling both windows and ubuntu. Is there a file format that both windos and ubuntu can read and write to? That way I can have the one drive shared for both Os's.

---

### Post by leg on 2007-04-24
Best option is probably fat32 for both to rw. Other than that you could try to set up a Samba share.

---

### Post by strabes on 2007-04-24
I would recommend having four partitions on your hard drive. Windows ntfs first, ubuntu ext3 second, swap third, and shared ext3 data partition fourth. This is how my computer is set up. You can use the driver from fs-driver.org to read and write to ext3 in windows. It works flawlessly. Make sure you install windows on the first partition before you install ubuntu - that's where it likes to be installed.

---

### Post by 50words on 2007-04-24
The only problem with using ext3 for a shared data partition is that Windows Desktop Search will not be able to index anything on an ext3 partition, including Outlook .pst files, if you store them there (although Google Desktop Search will), and online backup services like Carbonite will also not work with that partition.

For this reason, my shared data partition is NTFS and I use ntfs-3g to share. Beagle will index the NTFS partition just fine.

---

### Post by Harkainos on 2007-04-25
i really dont want to download a program to read the shared drive..... I am more interested in what filesystem works - read/write - both both OS's by default

---

