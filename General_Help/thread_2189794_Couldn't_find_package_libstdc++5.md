---
title: "Couldn't find package libstdc++5"
date: 2013-11-24
forum: General Help
---

### Post by mary.mortazavi on 2013-11-24
Hi dear all,
This is my first post in this forum and I'm new at Ubuntu. I'm using Ubuntu 10.04 lucid i686
I tried to install the library libstdc++5 by runing command sudo apt-get install libstdc++5 but it gives me the error below:

```
root@maryam-desktop:~# sudo apt-get install libstdc++5Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package libstdc++5

```

I tried several ways discussed in other threads but with no progress, didn't work for me or I didn't know how to use it!
I would be grateful if anyone helps me.
Best
Maryam

---

### Post by philinux on 2013-11-24
Lucid has reached end of life as you probably know. However that package is in the backports repo. You need to tick backports in your software sources.
[http://packages.ubuntu.com/lucid-backports/libstdc++5](http://packages.ubuntu.com/lucid-backports/libstdc++5)

Welcome to the forums as well.

---

### Post by mary.mortazavi on 2013-11-24
Thanks Philinux
I added the line [COLOR=#333333]deb http://[/COLOR]*cz.archive.ubuntu.com/ubuntu*[COLOR=#333333] lucid-backports main universe in sources.list and it worked;)[/COLOR]

---

