---
title: "restrict users to home directory"
date: 2008-03-09
forum: General Help
---

### Post by samona on 2008-03-09
[SIZE="2"]hi All,

I was wondering if there is a way to restrict users to their own home directories.  As of now any user can go to the root directory and browse all the files.  I don't want anyone but admins to be able to go up to the root directory.  Is there a way to restrict the users to their own home directories?[/SIZE]

---

### Post by yaknowwat on 2008-03-09
easiest way is to use the command line and use this
```
sudo chmod -R o-rwx '/root'
```
That should be it but i maybe wrong if someone wants to check it.

This article talks about permission in the command line.
[http://www.freeos.com/articles/4440/](http://www.freeos.com/articles/4440/)

Otherwise you have to login as root and do it manually for each user/group which can be a pain.

---

