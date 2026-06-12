---
title: "jedit - saving files"
date: 2008-01-15
forum: General Help
---

### Post by reflex on 2008-01-15
Hi,
first i want say that Ubuntu is great! 

I installed jEdit but i have problem with saving files, it always end with Cannot save error. When i run jEdit from terminal (sudo jedit) saving works.

Anyone can help?

Thx
Ref

---

### Post by x1a4 on 2008-01-15
Hi,

Since it works with root priviledges then this is a permissions problem.  Do you have write permissions to the file you're trying to write to?  Do you have write permissions to the directory you're trying to write to?  Run ```
ls -l
``` in a terminal to see who owns the file/directory you are writing to and what the permissions are.

---

### Post by reflex on 2008-01-16
I set permissions on whole directory (sudo chmod -R 777 /opt/lampp/htdocs/). I am making new file so i think there is no permissions  for it yet.

drwxrwxrwx 2 root   root    4096 2008-01-15 23:51 antikvariat
-rwxrwxrwx 1 root   root   30894 2007-05-11 14:40 favicon.ico
-rwxrwxrwx 1 nobody root     163 2003-10-31 22:15 index.html
-rw-r--r-- 1 root   root       6 2008-01-15 23:51 index.php
drwxrwxrwx 5 reflex reflex  4096 2008-01-14 23:26 ssf2
drwxrwxrwx 2 nobody root    4096 2008-01-14 19:21 webalizer
drwxrwxrwx 6 root   root    4096 2007-09-02 14:12 xampp

I am trying to save to the antikvariat directory.

Thanks for helping :]

---

