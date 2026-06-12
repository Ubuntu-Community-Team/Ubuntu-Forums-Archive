---
title: "Virtual Merge directory"
date: 2007-12-09
forum: General Help
---

### Post by ikus060 on 2007-12-09
Hi,

I'm searching a way to merge "virtually" multiple directory accessible via a samba share. I have 3 directory  2005 2006 2007 and in one month 2008. This directory contain a lot of file about 150 Gig. What I want, it's an other directory (ie: "all") that will contain all file present in each directory.

For example, If I have a file in /2006/data/user/Hello.txt, I want it to be accessible in /all/data/user/Hello.txt. I don't want it to be a copy, but something like a link. Also, If there is a file Hello.txt that are more recent in 2007, the Hello.txt file that are accessible in all directory must point to this file and not the older.

I'm sure that a lot of way I can do that, maybe with syslink, of some function in samba.

Thank for your help

---

### Post by maybeway36 on 2007-12-09
I would make a shared folder and put symlinks to 2005, 2006, 2007, and 2008 in them. That way, you would get a list of those folders when you connect.

---

### Post by ikus060 on 2007-12-09
It's not what I want. The end user must browser one directory (ie all) and see the content of directory 2006, 2007, ... In example, browsing the /all/data/ will show the content of /2006/data/ and 2007/data/. I don't want the user to search in each directory but only in "all" directory.

---

