---
title: "Cannot delete/move file"
date: 2020-01-08
forum: General Help
---

### Post by Philipp_Lehmayr on 2020-01-08
Even using sudo. I also cannot run "ls" in the folder where the file is located. The command line does nothing after I type these commands ("freeze") - I can't cancel the command with CTRL-C either! Even pressing TAB for filename autocompletion on that particular path will cause a freeze. (It works fine with other files/directories.)
stat: (Sorry, it's a German system.)
```
  Größe: 0              Blöcke: 5104       EA Block: 4096   Normale leere Datei
Gerät: fc01h/64513d     Inode: 1835014     Verknüpfungen: 1
Zugriff: (0644/-rw-r--r--)  Uid: ( 1005/  someuser)   Gid: (10008/sftpusers)
Zugriff    : 2020-01-08 10:54:56.774902766 +0100
Modifiziert: 2019-11-16 11:18:17.919942836 +0100
Geändert   : 2019-11-16 11:18:17.919942836 +0100
Geburt    : -

```
lsof returns nothing!

In the beginning I used lsof and found an old cron job that was still copying that file (even though its size is 0). I used kill -9 to get rid of that process. The freeze problem still occurs, though.

---

### Post by Impavidus on 2020-01-08
You can switch translation of the output off by prefixing the command with LANG=C_LANG:```
LANG=C_LANG stat filename
```But personaly, I don't mind reading german (I'm dutch). Showing the exact command you used may make life a little easier for those trying to help.

In any case, it looks like a weird file: an empty file taking 2552 kiB disk space. I think a filesystem check is the right thing to start with: [https://help.ubuntu.com/community/FilesystemTroubleshooting](https://help.ubuntu.com/community/FilesystemTroubleshooting)

---

