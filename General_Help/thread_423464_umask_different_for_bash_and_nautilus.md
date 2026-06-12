---
title: "umask different for bash and nautilus"
date: 2007-04-25
forum: General Help
---

### Post by bananabob on 2007-04-25
I have noticed that when you create a file under bash you get one set of permissions, and when you use nautilus Context Menu>Create Document>Empty File you get another.

> bananabob@thorium:~$ umask
0022
bananabob@thorium:~$ touch afiles.txt
bananabob@thorium:~$ ls afiles.txt -all
-rw-r--r-- 1 bananabob bananabob 0 2007-04-26 14:11 afiles.txt
<bfiles created by nautilus>
bananabob@thorium:~$ ls bfiles.txt -all
-rw------- 1 bananabob bananabob 0 2007-04-26 14:11 bfiles.txt

When you create the file using a program, for example gedit, you get the same permissions as with bash. 
> 
bananabob@thorium:~$ ls cfiles.txt -all
-rw-r--r-- 1 bananabob bananabob 5 2007-04-26 14:15 cfiles.txt


Why is there a difference, and is this a bug in nautilus?

---

