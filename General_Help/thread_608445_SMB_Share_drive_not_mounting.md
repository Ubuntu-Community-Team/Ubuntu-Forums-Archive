---
title: "SMB Share drive not mounting"
date: 2007-11-10
forum: General Help
---

### Post by duncan426 on 2007-11-10
I need help mounting a network drive.  this is what i have typed:

sudo mount -t smbfs //192.168.15.110/DISK%201 /mnt/Backup

and this is the result:

2942: tree connect failed: ERRDOS - ERRnosuchshare (You specified an invalid share name)
SMB connection failed

I made the dir in mnt, so i know thats not the problem.  Any help would be appreciated.  I am using 7.04.  I have a the drive mounted (I used connect to server option), so it is on my desktop and can access all files on the drive.  I want to mount it in /mnt/Backup

---

### Post by biovore on 2007-11-11
Looks like an Access denied from the server computer.. 
might need a -o username=<windows user>,password=<windows pass> on the end of that mount.. also might want to install the package smbfs

---

