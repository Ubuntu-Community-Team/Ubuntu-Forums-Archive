---
title: "Filesystem permission"
date: 2007-08-14
forum: General Help
---

### Post by YearZirO on 2007-08-14
im wonder how i can unlock the full permissions of my hard drive so i can Read,Write And Execute files im using ubuntu 6.06

thanks to anyone that can help

---

### Post by bren on 2007-08-14
if you are trying to write to an NTFS parition be aware that read only is default

to change this install as follwing from terminal

sudo apt-get install ntfs-3g ntfs-configure

then run 

gksudo ntfs-configure

if you have a different permissions problem then you can claim ownership of files using

chown yourusername:yourusername /yourdrivepath

and and then change permissions using chmod command

hope that helps
bren

---

### Post by YearZirO on 2007-08-16
> **bren said:**
> if you are trying to write to an NTFS parition be aware that read only is default

to change this install as follwing from terminal

sudo apt-get install ntfs-3g ntfs-configure

then run 

gksudo ntfs-configure

if you have a different permissions problem then you can claim ownership of files using

chown yourusername:yourusername /yourdrivepath

and and then change permissions using chmod command

hope that helps
bren


thanks

i got the following error..

broken@broken-laptop:~$ sudo apt-get install ntfs-3g ntfs-configure
Password:
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package ntfs-3g

---

### Post by bren on 2007-08-16
you need to make sure you have the right repositories (software sources installed)

go to a terminal and do 

cat /etc/apt/sources.list 

and post the results here

---

### Post by merlinus on 2007-08-16
```

sudo apt-get update && sudo apt-get install ntfs-config

```will install the ntfs-3g driver.

-merlin

---

