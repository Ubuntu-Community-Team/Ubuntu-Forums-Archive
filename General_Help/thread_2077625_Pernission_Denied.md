---
title: "Pernission Denied"
date: 2012-10-29
forum: General Help
---

### Post by Silvernail on 2012-10-29
Gnome3
12.04


What is going on with this 'Permission denied' responce?

> 
dave@Dafydd:/media/Teragb/music-storage/LauranOConnell$ ls -l
total 12
drwxrw-rw- 2 root root 4096 Oct 29 01:06 Covers
drwxrw-rw- 2 dave dave 4096 Jul 30 11:59 Everything
drwxrw-rw- 2 dave dave 4096 Jul 30 11:59 LauranOConnell
dave@Dafydd:/media/Teragb/music-storage/LauranOConnell$ cd Covers
bash: cd: Covers: Permission denied
dave@Dafydd:/media/Teragb/music-storage/LauranOConnell$ sudo cd Covers
sudo: cd: command not found
dave@Dafydd:/media/Teragb/music-storage/LauranOConnell$ cd Covers
bash: cd: Covers: Permission denied
dave@Dafydd:/media/Teragb/music-storage/LauranOConnell$ 

It will let me do this:
> dave@Dafydd:/media/Teragb/music-storage/LauranOConnell$ ls Covers
ls: cannot access Covers/Lauren O'Connell - Covers.zip: Permission denied
Lauren O'Connell - Covers.zip
dave@Dafydd:/media/Teragb/music-storage/LauranOConnell$ 


---

### Post by zombifier25 on 2012-10-29
```
drwxrw-rw- 2 root root 4096 Oct 29 01:06 Covers
```There's your problem. The folder Covers is owned by root, and its permission is set so that only root can read and write it.

Change the owner:
```
sudo chown -R dave:dave Covers
```

---

### Post by Silvernail on 2012-10-30
> **zombifier25 said:**
> ```
drwxrw-rw- 2 root root 4096 Oct 29 01:06 Covers
```There's your problem. The folder Covers is owned by root, and its permission is set so that only root can read and write it.


Thanks.
Question:
1. I have s hard drive with this problem. Can I use your example to fix that.

---

