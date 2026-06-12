---
title: "unique java problem"
date: 2004-11-05
forum: General Help
---

### Post by geoff on 2004-11-05
according to the [wiki entry](http://wiki.ubuntu.com/Java) for java installation, i added 

deb [http://jrfonseca.dyndns.org/debian](http://jrfonseca.dyndns.org/debian) ./

to my sources.list, and went to install the package 'j2re1.4' from it.

however, when it is installing, i get a liscence agreement thing come up.  i scroll through it, and when i get to the end, thats it.  can't get apt-get to finish the installation.  after aborting that, there is no way to remove it without reinstalling it, and no way to reinstall it without running into that liscence agreement again.

any help would be greatly appreciated.

---

### Post by az on 2004-11-05
It asks you if you agree yes or no.

Type yes if you agree.

---

### Post by geoff on 2004-11-05
i'm sorry, but it doesn't.  it just has 

(END)

at the end.

---

### Post by jwenting on 2004-11-05
Follow the installation instructions for Java elsewhere on the forums here and install the packages directly from Sun.
Those are far newer and have better performance as well.

---

### Post by geoff on 2004-11-05
that's what i plan on doing, but i really want to remove this broken package first, if for no other reason than for the satisfaction of not having a broken package on my machine.

---

### Post by geoff on 2004-11-05
found the problem, if anybody has this same exact problem, for this or any other program with an agreement, just hit the q key to get a yes no prompt!

---

