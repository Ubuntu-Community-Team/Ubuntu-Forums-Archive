---
title: "tasksel vs apt-get meta packages"
date: 2007-12-03
forum: General Help
---

### Post by bignose on 2007-12-03
Hello,

I'm setting up somewhat of a queer environment where I wanted to install LAMP-Server post install, instead of with the default install dialog. So I used this

sudo tasksel install lamp-server

And I got to thinking, there are times when I've wanted say KDE for example so i did this

sudo apt-get install kubuntu-desktop

So my question is this, why is there a separate tool ***tasksel*** when apt-get already exists with meta packages.

Is it just the fact that tasksel can have a GUI attached to it or something else?

Thanks folks.

---

### Post by bwald on 2007-12-03
Taskel is a package management system which groups packages by the tasks that they are used for.  The "lamp-server" from taskel is essentially a meta-package provided by Taskel to get all the packages needed for running that kind of server

Ubuntu also has many "meta-packages" which are Ubuntu-specific, such as kubuntu-desktop and ubuntu-desktop.

Essentially, its the same thing, Taskel just makes it easier to set up specific kinds of installations by installing all the right packages for it.  You can install the same metapackages with apt-get or aptitude if you wanted.

---

### Post by bignose on 2007-12-03
except oddly enough  you can't apt-get "lamp-server", correct me if i'm wrong.

---

### Post by louieb on 2007-12-03
> **bignose said:**
> except oddly enough  you can't apt-get "lamp-server", correct me if i'm wrong.
Just for grins I tried.
```
/home/lou%>sudo apt-get install lamp-server
[sudo] password for lou:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package lamp-server
/home/lou%>
```

---

### Post by bwald on 2007-12-03
You are correct, "lamp-server" is a taskel specific meta-package.  I was just trying to draw a correlation between Ubuntu meta-packages (such as kubuntu-desktop) and taskel meta-packages (such as lamp-server).  They are the same concept, but you can't mix which program (taskel or apt-get) runs them.

---

### Post by bignose on 2007-12-04
Right, so why  have 2 distinct tools that perform one task I guess should have been my orriginal question.

---

### Post by bignose on 2007-12-10
bumpola

---

