---
title: "FTP Help - Users and Folder rights"
date: 2008-01-03
forum: General Help
---

### Post by Solitary_ on 2008-01-03
Hi, I have looked at as many forums regarding FTP as my brain can handle and none of them tell me what I need to know, atleast not in a way that I seem to be able to understand.

I have an ubuntu 7.10 machine and have setup a sever.  And i am trying to give FTP rights to certain people for certain folders.

In windows I used guildftp and it let me create a user and specify what folders they had access to, for example i could create the user "ste" and give him access to "d:\music" and "d:\software"  but create the user "susan" and only give access to "d:\pictures"

Im trying to find out if I can create users for FTP in Ubuntu with individual access rights.

For example

the user "ste" with access to "/media/data/music/" and "/media/data/software" and the user "susan" with access only to "/media/data/pictures/"

The  /data/  folder is a secondary hard drive in NTFS format, I dont know if this will effect the ability to do what I mentioned above.

If anyone could help I would be very greatful.

Thanx

---

### Post by milton1 on 2008-01-03
you could create a new group, then make your new users all part of the appropriate "share" group. Then set permissions on your shared folders by group.

---

