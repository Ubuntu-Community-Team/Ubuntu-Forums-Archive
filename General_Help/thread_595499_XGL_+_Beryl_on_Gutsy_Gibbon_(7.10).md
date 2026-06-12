---
title: "XGL + Beryl on Gutsy Gibbon (7.10)"
date: 2007-10-28
forum: General Help
---

### Post by ShammyKon on 2007-10-28
I have searched around a while, and I was curious as to if there are any threads out there instructing on how to install Beryl and XGL on Gutsy Gibbon 7.10, with Nvidia graphics cards. Is this feat even possible? If so, any help is good help! Thanks!

---

### Post by matthew.lns1 on 2007-10-28
Does Compiz Fusion work? It is the newest version of Beryl and is installed and enabled by default and yes, the feat is possible

---

### Post by lexen on 2007-11-08
These two repositories should work for you, they worked for me.

deb [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) feisty main
deb-src [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) feisty main

The only problem is you need to download emerald from somewhere else.  If you use synaptic to install emerald, one of the dependencies, emerald-themes won't download, at least it didn't for me,  I had to download it from here:

[http://ftp.ussg.iu.edu/linux/ubuntu/pool/universe/e/emerald-themes/emerald-themes_0.2.1-0ubuntu1_all.deb](http://ftp.ussg.iu.edu/linux/ubuntu/pool/universe/e/emerald-themes/emerald-themes_0.2.1-0ubuntu1_all.deb)

And for the record, Compiz Fusion is NOT the latest version of beryl, it is an offshoot of beryl.  Beryl is still moving along without a problem.

I hope this helped.

---

