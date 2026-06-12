---
title: "Converting Fat32 Partition"
date: 2020-12-30
forum: General Help
---

### Post by rsteinmetz70112 on 2020-12-30
I have an 2TB external drive that Gnome Disks says is a Win95 Fat32 Partition. I would like to convert it to almost anything else. I tried using the Windows "convert" utility but got an error message saying there was not enough memory. Is there any utility out there tat will convert that partition? There is some information on it I'd like to retain without going to the trouble of copying it somewhere else, reformatting it then restoring the information.

---

### Post by dino99 on 2020-12-31
here is a guide : [https://www.wikihow.com/Format-a-Hard-Drive-Using-Ubuntu#](https://www.wikihow.com/Format-a-Hard-Drive-Using-Ubuntu#)

---

### Post by HermanAB on 2020-12-31
Note that you cannot convert it with your data in place.  So first make a backup, then use gparted to make a new partition and finally copy the data from the backup.

---

### Post by ajgreeny on 2020-12-31
What do you want to do with that disk? That will govern which format type you put on it; NTFS for Windows, probably ext4 for Linux.

---

### Post by rsteinmetz70112 on 2020-12-31
Thanks for the comments. I'm really just trying to find out if it can be converted to almost any because almost anything would be better than what I have but there are archive files on it that may be needed in the future. If necessary I can copy them and resote them.

---

### Post by rbmorse on 2020-12-31
It is necessary.

---

