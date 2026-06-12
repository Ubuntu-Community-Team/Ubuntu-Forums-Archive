---
title: "Property of folder not correct"
date: 2018-07-23
forum: General Help
---

### Post by mkbawalia on 2018-07-23
Sir, i have ubuntu 16.04 lts. When i check property of any folder it shows 507.2 gb even a small folder.
And i have 2 tb hard disk and only one home folder and it is showing home folder property only 507.2 gb. Thanks.

---

### Post by deadflowr on 2018-07-24
A folder can potentially use all available storage space, so it lists all available storage space the folder can use.
Since a folder is just a container for files.
Look at files and it should show the actual file sizes as those are set.

Why it shows as 507Gb rather than 2TB is because that's how much is left after the system allocated hard drive space to Ubuntu.
Open the Terminal program and run
```
sudo parted -l
df -h
```
the first command requires your user password and the password field inputs the password invisibly so type it as best you remember.
It will show the current hard drive layout which should show where the space is going.

The second command will show the current usages of the current operating system.

I think both can give a clear idea of where what is and or why.

---

