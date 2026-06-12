---
title: "Uninstall help..."
date: 2007-09-18
forum: General Help
---

### Post by obsines311 on 2007-09-18
I recently compiled a new version of glib and I wish to remove it. How do I remove the new version?

---

### Post by ruibernardo on 2007-09-18
Generally, when you compile a program from source, you run
```
sudo make install
```to install it. 

This generally works to uninstall it too. Go to the directory where the source are (where you complied it) and run:
```
sudo make uninstall
```

---

### Post by obsines311 on 2007-09-18
Thanks. And one more thing, sorry if this is OT, is it always necessary to run "make clean" after "make install"? What happens if you don't run "make clean"? Is it alright?

---

### Post by isaacj87 on 2007-09-18
I too would like to know the purpose of make clean...

I usually just 

make
sudo make install

---

### Post by isaacj87 on 2007-09-18
> **obsines311 said:**
> Thanks. And one more thing, sorry if this is OT, is it always necessary to run "make clean" after "make install"? What happens if you don't run "make clean"? Is it alright?

I found this:
> 

< Cleaning up the mess >

I bet you want to save some disk space. If this is the case, you'll want to get rid of some files you don't need. When you ran make it created all sorts of files that were needed during the build process but are useless now and are just taking up disk space. This is why you'll want to make clean:

me@puter: ~/dls/pkg$ make clean

However, make sure you keep your Makefile. It's needed if you later decide to uninstall the program and want to do it as painlessly as possible!


Can someone confirm this for us noobies? :)

---

