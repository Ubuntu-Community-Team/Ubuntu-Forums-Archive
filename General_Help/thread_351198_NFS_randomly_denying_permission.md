---
title: "NFS randomly denying permission"
date: 2007-02-01
forum: General Help
---

### Post by dallingham on 2007-02-01
I've migrated to a new NFS and NIS server. The new server seems to be doing some very strange things. NFS seems to be randomly denying access to files that I own.

[FONT="Courier New"]$ ls
8g3rtccm.default  pluginreg.dat  profiles.ini
$ ls -l
total 16
drwxrwxrwx 6 dona vlsi 4096 2007-02-01 14:29 8g3rtccm.default
-rw------- 1 dona vlsi 6651 2007-02-01 14:09 pluginreg.dat
-rw-r--r-- 1 dona vlsi   94 2007-02-01 13:34 profiles.ini
$ ls
ls: .: Permission denied[/FONT]

As you can see, the third time I try to list the files in the directory, I get a permission denied error. Any ideas on what is wrong?

---

