---
title: "Make Windows Disk Not Require Password"
date: 2007-07-14
forum: General Help
---

### Post by XMike14x on 2007-07-14
Well I have a quick question. I'm a n00b to Ubuntu so its probably simple to answer. Every time I load Ubuntu I have to enter my password to access my Windows hard drive. Can someone tell me a permanent workaround?

---

### Post by brent113 on 2007-07-17
I'll do my best, let me know if any of these work:

In a terminal you can change the owner of a folder and all it's subfolders to your user (if it's root) by using

```

sudo chown -R username:username directory

```

and then you can give yourself (and everyone else) read/write permissions by using

```

sudo chmod -R 777 directory

```

Obviously put your username in for username and put the path to the folder it's mounted in for directory.  If you don't want to give everyone read/write you can use "man chmod" to read it's help file.

---

### Post by splintercellguy on 2007-07-17
If you add your NTFS partition to your fstab, I believe the root password request goes away.

---

### Post by ugm6hr on 2007-07-17
Follow this:
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

