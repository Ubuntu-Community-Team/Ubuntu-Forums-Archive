---
title: "need help installing gambas 3"
date: 2012-11-17
forum: General Help
---

### Post by tech7 on 2012-11-17
I'm using Xubuntu 12.04 and am having some difficulties getting Gambas 3 to install.

I've read on the Gambas website that there is some kind of issue with the more recent Ubuntu repos not having the right packages, but I've followed it's instructions and still cannot get Gambas 3 to install properly.

The website says to add their repo
```
$ sudo add-apt-repository ppa:nemh/gambas3
```

I've done that.  Install via terminal using apt seems to go just fine.  But, the software will not load when I either click on it in the menu or call it in terminal.

When I call it in terminal, this is the error I get:
```
root@burrito-Latitude-D600:/home/burrito# gambas3
ERROR: #2: Cannot load class 'TableView': Cannot load parent class: Cannot load class 'GridView': Unable to load class file

```

Any help would be greatly appreciated!

---

### Post by rai4shu2 on 2012-11-17
I don't know much about gambas or the latest version, but I am curious why you run it as root. That seems like a huge mistake, to me.

---

### Post by tech7 on 2012-11-17
I've tried to run it as user and as root.  Nothing works.  I think that particular paste was just from one of the attempts at getting it to run shortly after having 'installed' it via terminal as root.

---

### Post by tech7 on 2012-11-17
I get this error even whether I compile the package from source, from synaptic, apt, software center.

---

### Post by rai4shu2 on 2012-11-17
Try purging the old install completely, then reinstall. That's been reported to fix that issue.

[http://gambasdoc.org/help/install/ubuntu?v3](http://gambasdoc.org/help/install/ubuntu?v3)
[http://gambas.8142.n7.nabble.com/Cannot-load-parent-class-td46.html](http://gambas.8142.n7.nabble.com/Cannot-load-parent-class-td46.html)
[https://bbs.archlinux.org/viewtopic.php?id=139430](https://bbs.archlinux.org/viewtopic.php?id=139430)

---

### Post by tech7 on 2012-11-18
I'm sorry.  I guess I should have mentioned that I have done that several times.  I have also purged the dependencies several times before reinstall attempts or compilation.

---

### Post by kalaharix on 2012-11-23
Just had a bit of time to install Xubuntu 12.04 32bit and then Gambas3 by the method you describe.

It works but I (and others on the gambas forum) have had problems like yours over the last week. I suspect a dependency had changed and the effect on Gambas now been repaired.

Have you managed to install since your last post?

rgds

---

### Post by tech7 on 2012-12-05
Nope.  Actually, I ended up installing Ubuntu 10.04.  I was having so many problems with many different things.  All of the issues I knew to either be non-existent in 10.04 or I already know how to fix them.  Installing JRE, netbeans, Gambas3, and several other tools that I prefer are difficult or impossible in Xubuntu 12.04 so I forsaken the want for a newer OS for the convenience of one that I was already very familiar with.

---

