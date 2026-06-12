---
title: "Permissions and Me - They don't like me"
date: 2008-05-01
forum: General Help
---

### Post by keylime on 2008-05-01
I am having some trouble deleting one file from this folder. When I do, it refuses to do so.

Here's a sample of the text:

-rw-r--r-- 1 root    root     96 2008-05-01 13:41 mimeinfo.cache
-rwxrwxrwx 1 keylime keylime 944 2008-05-01 13:41 opera.desktop

I claimed ownership of the opera file, and gave all users rwx (777) permissions. It still won't delete. 

How can I delete this then?

Thanks in advance.

---

### Post by imT on 2008-05-01
try with sudo or from guy, with "gksudo nautilus"; usualy works for me :)

---

### Post by keylime on 2008-05-01
I did try the sudo but it didn't like me. Strange I know.

However I did manage to rid of it via sudo shred. Thanks for the help.

---

