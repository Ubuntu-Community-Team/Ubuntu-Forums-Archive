---
title: "torrentflux &amp; proftpd"
date: 2008-06-26
forum: General Help
---

### Post by tfcrazy on 2008-06-26
Hello,

First of all i would like to say thanks for the great guides that have helped me numerous times.

Im using Ubuntu 6.06LTS on my server and i have got the latest torrentflux-b4rt installed along with the latest proftpd.

Now my problem is that i want to be able to edit/delete the files that torrentflux creates from the separate ftp user but all i get is error 500 and permission denied.  So I know that this means that the chmod permissions of the directories within torrentfluxe's download folder get automatically set to 755 thus not allowing the ftp user to edit or delete the files only view them (so to say).

This also happens the other way around as in i put a directory within the torrentflux download folder and i am not abled to edit or delete the files from within torrentflux.  So i know that the ftp is creating the directories and files within them with 755 permissions.

Is there any way to make it so that torrentflux and ftp create the directories and files with 775 permissions?

Thank you in advance

tfcrazy

---

