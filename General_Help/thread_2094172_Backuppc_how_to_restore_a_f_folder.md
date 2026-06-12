---
title: "Backuppc how to restore a f folder"
date: 2012-12-13
forum: General Help
---

### Post by natostanco1980 on 2012-12-13
I have a backup made with backuppc that contains all the encrypted files (starting with f), I want to save all of them in a readable archive, the thing is that I have this folder in a different OS where backuppc is not even configured, how to do so? Bacuppc tar, zip and restore functions require some parameters from a configured backuppc installation, while I don't have it, the only thing I could do is using Backuppc_zCat on all the files recursively...(and I might need help creating this script...)
or am I missing something? please help!

---

### Post by natostanco1980 on 2012-12-13
```
find ./ -type f | while read line; do
rname=`echo $line | cut -c4-`
rname=`echo ${rname} | sed 's/\/f/\//g'`
echo $rname
mkdir -p $(dirname /root/backups/"$rname");
rname=`echo $line | cut -c4-`
sname=`echo ${rname} | sed 's/\/f/\//g'`
/usr/share/backuppc/bin/BackupPC_zcat ./"$line" &> /root/backups/"$sname"
done
```

---

