---
title: "Cannot read smbmounted share allthough permissions ok"
date: 2008-05-07
forum: General Help
---

### Post by cleca on 2008-05-07
Hi !

I have a file mounted remotely which I cannot read although the file is readable and the fs is mounted readable. I can read other files on that share, but I cannot read this specific file. It is not a system special file but just a normal .gz file. I just do not understand this.

Any help ?

Some more details:

root@bubu:/mnt/INN/UNAGON-NG/BERKELEY-DB# ls -algu
total 9068
drwxrwxrwx 1 root       0 2008-05-07 22:37 .
drwxrwxrwx 1 root       0 2008-05-07 22:31 ..
-rw-r--r-- 1 root       0 2008-05-08 01:58 asd
-rwxrwxrwx 1 root 9281894 2008-05-07 21:44 db-4.5.20.tar.gz
root@bubu:/mnt/INN/UNAGON-NG/BERKELEY-DB# gunzip db-4.5.20.tar.gz 
gzip: db-4.5.20.tar.gz: Permission denied
root@bubu:/mnt/INN/UNAGON-NG/BERKELEY-DB# chmod -v 777 db-4.5.20.tar.gz 
mode of `db-4.5.20.tar.gz' retained as 0777 (rwxrwxrwx)

When straceing gunzip I get

open("db-4.5.20.tar.gz", O_RDONLY|O_NOCTTY|O_NONBLOCK|O_LARGEFILE|O_NOFOLLOW) = -1 EACCES (Permission denied)

When stracing chmod I get

fchmodat(AT_FDCWD, "db-4.5.20.tar.gz", 0777) = 0

so the chmod is done.

Mount shows the share as

//tala/INN on /mnt/INN type cifs (rw,mand)

I can write, read and edit other files on this share but I cannot do so with the .gz file.

The share lives remotely at Windows XP SP2 and is a NTFS share open for remote access.

The machine I am doing the accesses from onto this share is a completely up to date Ubuntu running 2.6.24-16-generic kernel.

I can read access and decompress the .gz file on the remote Windows machine. I can read access the decompressed files on the Ubuntu machine. But I cannot read access the .gz file.

So :confused: exactly points out my feelings.

Any ideas ?

---

