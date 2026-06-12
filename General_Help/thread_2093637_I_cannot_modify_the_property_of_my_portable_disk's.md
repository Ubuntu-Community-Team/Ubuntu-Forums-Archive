---
title: "I cannot modify the property of my portable disk's file"
date: 2012-12-11
forum: General Help
---

### Post by iPhilip on 2012-12-11
I write a c program on my portable disk and I compile it into a executive file( say a.out). I use the command ls and see it is -rw-r--r-- ,so I type the command: sudo chmod  g+x a.out
and execute it.But after that the ls command's result is still -rw-r--r--.And indeed, I cannot execute it in terminal: ./a.out.
When I copy the a.out to my pc's hard disk ,the sudo chmod g+x a.out can change the file's property.
My english is poor,I need ur help!
Thank u!

---

### Post by dannyboy79 on 2012-12-11
what filesystem is your portable disk formatted as? if it's NTFS, you can't control the permissions of the file then

---

### Post by rnerwein on 2012-12-11
> **iPhilip said:**
> I write a c program on my portable disk and I compile it into a executive file( say a.out). I use the command ls and see it is -rw-r--r-- ,so I type the command: sudo chmod  g+x a.out
and execute it.But after that the ls command's result is still -rw-r--r--.And indeed, I cannot execute it in terminal: ./a.out.
When I copy the a.out to my pc's hard disk ,the sudo chmod g+x a.out can change the file's property.
My english is poor,I need ur help!
Thank u!
hi
do you get some error messages when you try to change the permission or when try to run your a.out ?
if your portable disk is pluged in show us how it is mounted
in a terminal type: mount
then: ls -l a.out
and : file a.out

post the output of the three commands and if present the error messages  that we can get more informations.

---

### Post by iPhilip on 2012-12-12
yes,my portable file system is ntfs,is there any method?
Thank u!
> **dannyboy79 said:**
> what filesystem is your portable disk formatted as? if it's NTFS, you can't control the permissions of the file then

---

### Post by dannyboy79 on 2012-12-12
nope, you can't control permissions from linux on a NTFS filesystem

---

