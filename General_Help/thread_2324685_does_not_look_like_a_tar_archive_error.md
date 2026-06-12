---
title: "does not look like a tar archive error"
date: 2016-05-15
forum: General Help
---

### Post by neil41 on 2016-05-15
/usr/local/src# gunzip < /mnt/MySQL/Linux/tarballs/source/mysql-4.0.21.tar.gz | tar xf -

bash: /mnt/MySQL/Linux/tarballs/source/mysql-4.0.21.tar.gz: No such file or directory

tar: This does not look like a tar archive

tar: Exiting with failure status due to previous errors



could anyone please help me on dealing with the above error.

---

### Post by steeldriver on 2016-05-15
Well if the tar.gz file doesn't exist, then there is nothing for tar to extract (hence "does not look like a tar file")

What are you trying to do, exactly? Modern versions of tar are capable of uncompressing gzipped files directly

---

### Post by nerdtron on 2016-05-15
I think your syntax is wrong, you should the -c option and not the < redirector:
```
 [root@goddard ~]# gunzip -c latest.tar.gz | tar xf - 
```

OR:
Check with the file command if it's really a compressed tar archive.
```

[root@goddard ~]# file latest.tar.gz
latest.tar.gz: gzip compressed data, from Unix, last modified: Wed Dec  9 07:45:32 2015

```

If it is, then you can uncompress it and un-tar with a single command below
```
[root@goddard ~]# tar -zxvf latest.tar.gz 
```

---

### Post by kjohri on 2016-05-17
Suppose there is a tar archive, x.tar.gz. You can give the following commands, 

$ gunzip x.tar.gz
$ ls -ls x.tar
18080 -rw-rw-r-- 1 abc abc 18513920 May 17 12:39 x.tar
$ file x.tar
x.tar: POSIX tar archive (GNU)
$ tar -xvf x.tar

The command "file x.tar" tells what kind of file it is. The last command extracts the files from the archive.

---

