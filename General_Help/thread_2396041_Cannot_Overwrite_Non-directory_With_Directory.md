---
title: "Cannot Overwrite Non-directory With Directory"
date: 2018-07-10
forum: General Help
---

### Post by lawrence-joy on 2018-07-10
I am trying to transfer a directory with files from an internal drive to an external USB-stick drive. I get the dreaded "Cannot overwrite non-directory with directory". I execute the command 'file ~/4R5_V_sply' on the external USB-stick and it comes back with "...: ASCII text", which is all well and good. Then I execute the command 'file ~/4R5_V_Sply' on the USB-stick and it comes back with "...: ASCII text". This to me is not good, I think it should come back with "file not found" as the 2nd file uses an upper case S versus a lower case s that the actual file has. I thought that the Ubuntu OS knows the difference as it does make a difference when typing commands? Are file names an exception? The directory name with files that I am trying to transfer is "4R5_V_Sply". The "4R5_V_sply" is a regular file as denoted by the hyphen in the first position of the permissions list while "4R5_V_Sply" is a directory as indicated by a "d" in the first position of the permissions list. What do I need to do?

---

### Post by vanadium on 2018-07-10
Ubuntu is case sensitive with filenames as well. The issue here is that the file system on your USB drive is only partially case sensitive. You will not have the issue if the USB is formatted in a fully case sensitive file system such as ntfs and the native linux file systems.

---

### Post by col48 on 2018-07-10
At least you were warned.

If the USB already had an ordinary S file and you copied over an ordinary s file but different from the S file already there you could have lost the S file.

Safer not to rely on case-sensitivity to distinguish files or directories.  Especially as S and s can look very similar!

---

