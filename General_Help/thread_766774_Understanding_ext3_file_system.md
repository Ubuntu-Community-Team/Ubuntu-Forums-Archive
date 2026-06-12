---
title: "Understanding ext3 file system"
date: 2008-04-25
forum: General Help
---

### Post by Barry53 on 2008-04-25
Where would I go to find an explanation of the ext3 file system used in Gutsy. I am working on a backup solution and realize some of the directories in the file system are pseudo and shouldn't be backed up. I am new to Linux and think an explanation of each directory and its use would be helpful. Thanks in advance.

---

### Post by chrisccoulson on 2008-04-25
The purpose and function of the directories is not related to the filesystem type (ext3) that you speak of. A Linux system could be installed on one of many different filesystem types available (ext2, ext3, reiserfs, JFS etc), but the structure and purpose of the files and folders would be the same.

If you want to know how your systems files and folders are organized (and their purpose), then you're best off having a look at the [**_FHS 2.3 PDF_**]("http://www.pathname.com/fhs/pub/fhs-2.3.pdf") or having a look [_**here**_]("http://www.tuxfiles.org/linuxhelp/linuxdir.html")

---

### Post by articpenguin on 2008-04-28
if you want to know the internals of the ext2 system go here
[http://e2fsprogs.sourceforge.net/ext2intro.html](http://e2fsprogs.sourceforge.net/ext2intro.html)

ext3 is just ext2 with a journal.

---

