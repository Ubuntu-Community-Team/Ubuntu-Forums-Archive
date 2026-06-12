---
title: "How do I install drop box on 18.04?"
date: 2019-06-01
forum: General Help
---

### Post by Tom_Carr on 2019-06-01
How do I install drop box on 18.04?  I expected to find it in the software center but it is not there.

---

### Post by deadflowr on 2019-06-01
Should be the nautilus-dropbox package.
The software store if fickle.

---

### Post by Tom_Carr on 2019-06-01
That worked.  Thanks.  
It really is too fickle.  How would anyone know that without asking?  I wonder why someone hasn't fixed it?

---

### Post by deadflowr on 2019-06-01
An old bug related to software not showing all apps it really should:
[https://bugs.launchpad.net/ubuntu/+source/gnome-software/+bug/1579415]("https://bugs.launchpad.net/ubuntu/+source/gnome-software/+bug/1579415")
There are probably  couple dozen more bug reports like that too.

For what it's worth I see Dropbox in software on my 18.04 install:
[ATTACH=CONFIG]283352[/ATTACH]

Not sure why it shows for some and not for others.
Fickle seems more and more apropos.

---

### Post by ajgreeny on 2019-06-01
Not showing all available packages is one of the disadvantages of the "software centre" or whatever it's now called, and definitely one of the advantages of synaptic which will show all the dropbox packages available; it currently shows seven of them if you search package names only using "dropbox" as the search term.

Synaptic used to be the default GUI package manager of Ubuntu, and still is installed by default in debian itself and many of the ubuntu based distros; I think it's in Mint by default but it's a long time since I looked at Mint.
It is still in the repos of all of the Ubuntu family as far as I'm aware and is usually the first of the additional packages I install after installing a Ubuntu distro.

---

### Post by Tom_Carr on 2019-06-01
Thanks for your help.

---

