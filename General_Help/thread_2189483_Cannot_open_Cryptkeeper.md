---
title: "Cannot open Cryptkeeper"
date: 2013-11-22
forum: General Help
---

### Post by rdh61 on 2013-11-22
I have installed Cryptkeeper on a Mac iBook G4 running Lubuntu 13.10. It is the powerpc package.

When I try to open it with System Tools -> Cryptkeeper, nothing happens.

When I try to open it with a terminal, I get:

```
robert@lubuntu-ibookg4:~$ cryptkeeper
Segmentation fault (core dumped)
robert@lubuntu-ibookg4:~$ 

```

Any help gratefully received.

Many thanks.

---

### Post by wh1zz0 on 2014-01-08
Yes I am still having the same issue... Have you been able to solve this problem?

---

### Post by rdh61 on 2014-01-08
No, I gave up on it. Instead I'm using encfs from the command line.

---

### Post by deadflowr on 2014-01-08
If you want an alternate cryptkeeper gui, look here
[http://www.webupd8.org/2013/05/gnome-encfs-manager-cryptkeeper.html](http://www.webupd8.org/2013/05/gnome-encfs-manager-cryptkeeper.html)

I have cryptkeeper on precise and on the dev version trusty(for now).
The precise version opens fine, and the trusty version is tempermental.
I, too, find myself using the cli from time to time on the newer version.

---

### Post by rdh61 on 2014-01-09
Thanks, I'll give it a try.

---

### Post by rdh61 on 2014-01-09
Gnome Encfs Manager works fine. Thanks again.

---

### Post by wh1zz0 on 2014-01-10
I found a solution. 

You just simply need to double click on it from the main menu rather than clicking on it once. If you double-click it becomes visible on the panel, then you can proceed.

Hope this helps someone...

---

