---
title: "Can't change permission using Gnome Commander"
date: 2016-03-09
forum: General Help
---

### Post by messiah2 on 2016-03-09
I can't change permissions for any root files or folders. How to fix this?

---

### Post by DuckHook on 2016-03-09
Graphical file navigators are designed by default not to change root file permissions. This is done for reasons of safety because, as a rule, root-owned files rarely need their permissions changed. Can you tell us why you want to do this?

---

### Post by messiah2 on 2016-03-09
I got installed xampp and I'm copy my files from windows to /opt/lampp/htdocs/ and all files have root owner so I can't edit any files.

---

### Post by DuckHook on 2016-03-09
I don't use LAMP so my knowledge is limited. That said, the usual technique to deal with  root-owned files is not to change permissions , but to edit them in the command line with```
sudo nano /path/to/file
```To learn about permissions and how to change them:

[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

---

### Post by messiah2 on 2016-03-10
Solved. I set chmod 777 to htdocs using terminal.

---

### Post by Bucky Ball on 2016-03-10
Great. Please see the first link in my signature at the bottom of this post. Thanks.

---

### Post by yancek on 2016-03-10
If you copied files from another operating system  to the location you refer to, you must have done it as root so obviously all the directories/files would be owned by root.  You can access them as root user and change anything.  Changing the owner:group to www-data:www-data and putting your user in the www-data group is the standard method rather than giving complete permission to delete anything on that server to anyone with access to the computer.

---

