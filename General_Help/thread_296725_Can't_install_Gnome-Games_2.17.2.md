---
title: "Can't install Gnome-Games 2.17.2"
date: 2006-11-10
forum: General Help
---

### Post by La muerte del DIos on 2006-11-10
Hi, i've just download the *.tar.gz package of the new Gnome Games and I really doesn't know how to install them and substitute the old ones. :confused: Can someone please help me here?

---

### Post by ciscosurfer on 2006-11-10
The package gnome-games to which you refer can be downloaded through the repositories as a .deb package (whether you're running Dapper or Edgy).  

In other words, there is no reason to try to build it from source.  

To install gnome-games, from within a terminal, enter the following```
sudo aptitude install gnome-games
```

---

### Post by La muerte del DIos on 2006-11-10
Can you please tell me which repositories? Because in the "default" ones (universe, multiuniverse, etc) there's only version 1.*.*.* and I want to install 2.17.2 mostly because of the online features. Also it never hurts to learn how to compile.

---

### Post by ciscosurfer on 2006-11-10
The gnome-games in the main Edgy repo is version 1:2.16.1 so that means it's version 2.16

It's important to note that according the [this page]("http://www.gnome.org/projects/gnome-games/"), even number releases are stable and odd numbered one's (like 2.17) are for testing.

If you want to use the 2.17.2 version, you can download it from their FTP site, extract it, and compile it.  Go to [this page for instructions]("http://monkeyblog.org/ubuntu/installing/") on how to do this.

I would recommend substituting **checkinstall** for **make install** that way you can package it and it makes it a whole lot easier to remove it.

So, you can remove your current version of gnome-games by running the following in a terminal```
sudo dpkg -r gnome-games
OR
sudo aptitude remove gnome-games
```And then compile your new gnome-games, package it up with **checkinstall** instead of issuing **make install**, and then you're all set.

---

### Post by La muerte del DIos on 2006-11-10
Thank very much. I'll give it a try.

---

