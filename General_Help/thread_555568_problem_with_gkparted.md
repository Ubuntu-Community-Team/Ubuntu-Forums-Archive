---
title: "problem with gkparted"
date: 2007-09-20
forum: General Help
---

### Post by maaylix on 2007-09-20
I`m trying to format my second hard drive to create a home partition in it. To do that, I`m using [this guide](http://www.psychocats.net/ubuntu/separatehome).

The problem is that when I try to create my new partition with gkparted, the hard drive I`m trying to partition is suddenly mounted during the partition operation and gives me the following error 

```
gtkmm-ERROR **: file treeiter.cc: line 214 (const Gtk::TreeNodeChildren& Gtk::TreeRow::children() const): assertion failed: (!is_end_)
aborting...

```

---

### Post by louieb on 2007-09-20
its a **bug in hal** go to system > prefrences > removable media and uncheck the  auto mount boxes.  That will keep it from mounting the drive while your in GParted.

---

### Post by maaylix on 2007-09-20
Thx louieb, that`s all it took to get gkparted to work!

---

