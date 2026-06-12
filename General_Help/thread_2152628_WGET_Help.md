---
title: "WGET Help"
date: 2013-06-08
forum: General Help
---

### Post by dustywb82 on 2013-06-08
Hi, I'm trying to use wget to automate some file downloading and seem to be having some trouble getting the syntax just right, was wondering if someone with a bit more experience could assist me here.

I'm using:
wget -x -nH --directory-prefix=c:\directory\structure\here -r -np --cut-dirs=4 --reject=html [http://www.example.com/directory/structure/here/folder2download](http://www.example.com/directory/structure/here/folder2download)

This downloads the proper files to the proper directory, but then it moves up 1 directory on the web and downloads all the files/folders in the parent directory and puts them all in c:\directory\structure\here from reading online I thought -np would stop this am I wrong? Or is something else going on? O also this isn't actually running on ubuntu I'm using wget for windows which uses the same commands/switches as wget in linux/ubuntu as far as I can tell.

---

### Post by dustywb82 on 2013-06-09
No-one out there know anything about wget???

---

### Post by ahallubuntu on 2013-06-09
~

---

