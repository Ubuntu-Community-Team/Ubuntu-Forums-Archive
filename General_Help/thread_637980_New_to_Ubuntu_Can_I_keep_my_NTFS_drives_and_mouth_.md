---
title: "New to Ubuntu: Can I keep my NTFS drives and mouth them?"
date: 2007-12-11
forum: General Help
---

### Post by codeblue2k on 2007-12-11
So I am new to Ubuntu. I have an old PC that I was thinking I would turn into a Media server and store all of my movies, and MP's on. I will format the main dive as needed, but the drive that currently has my media files on it is formatted int NTFS. Do I need format it?

---

### Post by rkrash3423 on 2007-12-11
No u don't have to format, and yes u can mount them. I have a windows partition along with a linux partition and an ntfs partition to share between the two. works great. ubuntu 7.10 has ntfs support by default. they will auto mount though, so you'll have to comment out (#) your windows partition in /etc/fstab if u have one and u don't want it to auto mount by default. if your ntfs drive won't auto mount by default then I may be able to help u. let me know....

---

