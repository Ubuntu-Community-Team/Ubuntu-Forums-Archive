---
title: "Can't share files on ntfs partition through samba"
date: 2007-04-19
forum: General Help
---

### Post by arsenic23 on 2007-04-19
Edgy never quite worked for me, so my main PC has been Dapper up until last night.  Backed up my ~/ , nice clean format and reinstall, and almost everything is working as good or better then before.  I just have one problem, I can't share files that are on my ntfs partition.  Perhaps I'm forgetting or missing something?

I have two partitions on the same drive as my /, one is ext3 mounted at ~/ext3, the other is ntfs, mounted at ~/ntfs.  My archived music and movies are on the ntfs partition, and they need to be shared so that I can listen to/watch them in other rooms.  Unfortunately anything I try to share in the ntfs partition, or the partition itself comes up as:
> The Folder contents could not be displayed.
"foldername" couldn't be found. Perhaps it has recently been deleted.

I'm sure I had this working in dapper with the exact same setup, I just can't remember whether there was a trick to it or not.

---

### Post by attelas on 2007-05-02
I encountered  the same problem. Did you receive the same message as I did when trying to share a directory? (Message stating" access denied")
Must be a matter of rights, that I'm sure.
With the command ls-l I see drwxrwx--- . May be the three --- indicate what I'm missing. (and you as well).

---

### Post by gabng on 2007-05-10
Hi, just wondering if this has been resolved since I'm having the same problem.
I mounted my ntfs parition on /media/sda1 using ntfs-3g, I tried to share it using NFS.  The NFS client sees the shared folder, but when I mount it, it retruns:
```
mount: 192.168.1.7:/media/sda1/folder failed, reason given by server: Permission denied
```
I would like to know if this is due to limitation of ntfs-3g or am I missing something?

---

### Post by kelvin spratt on 2007-05-10
Both edgy and fiesty use the latest ntfs 3g but it needs enabling first in fiesty its in add remove i think if you have probs download the dreaded by some Automatix and you will find it in their i personally use the Automatix version as it unmounts and remounts my 3 ntfs partitions better i can write direct to the partition before if i dowloaded it would not open a ntfs partition to download and i had to cut and paste now its direct to ntfs

---

### Post by ewookie on 2007-06-07
i have a similar or same problem.  i can share the whole drive, but that's not what i want to do.  i want to share just the videos folder on the ntfs partition, but it doesn't work.

---

