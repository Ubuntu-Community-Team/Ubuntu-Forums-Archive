---
title: "0 Bytes Available"
date: 2020-12-05
forum: General Help
---

### Post by manikinxvx on 2020-12-05
I was recovering deleted files(TestDisk) and there was an interuption to the electricity during the process 
After booting up again I discovered I had 0bytes available when I should have had Gbs of available space. I located the archive file made by TestDisk and deleted, but that did nothing to clear space. I then did both a clean and autoclean in Terminal... still nothing.

Please advise. Thanx in advance.

---

### Post by TheFu on 2020-12-05
Figure out where all the storage s being used. There are many different ways.

Figure out which file system(s) are out of storage:
```
df -hT -x squashfs -x tmpfs -x devtmpfs
```

Then figure out which subdirectories are using all the storage. Say /var s the filesstem that is full,
```
cd /var
du -sh * | sort -h
```
That will make a sorted list.
cd down into the worst offender and repeat.

You can also use **ncdu** to search drectories.

To find large files, use find.
```
find / -type f -size +1G
```
Restrict the directories to be searched as much as possible.  Change the size as needed.  This is a slow method, but faster than ncdu.

---

