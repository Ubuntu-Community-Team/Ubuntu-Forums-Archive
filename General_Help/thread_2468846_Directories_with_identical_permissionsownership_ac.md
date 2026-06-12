---
title: "Directories with identical permissions/ownership accessibility problem"
date: 2021-11-11
forum: General Help
---

### Post by Dave_Davis on 2021-11-11
on my Ubuntu server I have two folders that have identical ownership and permissions

dmd@UB230:/mnt/development/websites$
drwxrwxrwx 14 dmdefd dmdefd 4096 Nov 10 14:59 music/

and

dmd@UB230:/mnt/users$ 
drwxrwxrwx  5 dmdefd dmdefd 4096 Nov 10 15:29 music/

I can write to the latter and create directories.

However, any time I try to create a directory or write to a file (using windows) i get an error saying I don't have permission.

I've been at this all afternoon.  What am I missing?

Thanks

---

### Post by TheFu on 2021-11-11
Unix permissions have nothing to do with Windows.  
Having 777 permissions means you don't care at all about security.

Are you doing something with samba?
Or is it some other method?
Are the file systems Linux native or Windows stuff?  Windows file systems don't care about Unix permissions. The permissions can only be controlled by mount options.

A few commands to provide more relevant information:
```
df -Th -x squashfs -x tmpfs -x devtmpfs
mount |grep /mnt
testparm -s # if using samba
```

---

