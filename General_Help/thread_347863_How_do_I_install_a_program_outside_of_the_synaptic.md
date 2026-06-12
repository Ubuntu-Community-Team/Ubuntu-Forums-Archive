---
title: "How do I install a program outside of the synaptic manager [Resolved]"
date: 2007-01-27
forum: General Help
---

### Post by east_villager on 2007-01-27
I've been using Ubuntu for a month or so and trying to figure things out.  

I've downloaded a password safe program and would like to install it, but can't figure it out.  There are a couple of password programs listed in the Synap. Manager and those won't install due to conflicts.  Can't get anywhere with that either. Any help out there?

---

### Post by ~LoKe on 2007-01-27
What kind of file is it?  .deb?

If it is, then double click it and click "install package".  Or, from the terminal:
```
sudo dpkg -i package.deb
```

If it's an archive, extract it wherever you want, then load up the terminal, then **cd** into the directory:
```
cd package
./configure
make
sudo make install
```

---

### Post by aysiu on 2007-01-27
What's the name of the program?

---

### Post by east_villager on 2007-01-27
Its a tarball ---  tar.gz

---

### Post by east_villager on 2007-01-27
Password Safe

---

### Post by aysiu on 2007-01-27
By the way, if you're getting dependency conflicts, you probably have a bad repositories list.

You can get a fresh repositories list [here](http://www.psychocats.net/ubuntu/sources). Afterwards, click Reload, and then you should be able to install whatever you want from Synaptic.

---

### Post by east_villager on 2007-01-27
Thanks aysiu.  I reloaded the repositories and was able to load a program to try.  Appreciate your help.

---

### Post by aysiu on 2007-01-27
No problem. Glad it worked out for you.

---

