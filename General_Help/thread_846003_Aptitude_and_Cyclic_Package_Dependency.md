---
title: "Aptitude and Cyclic Package Dependency"
date: 2008-07-01
forum: General Help
---

### Post by Frozsyn on 2008-07-01
Hello,

This is my first post, and I didn't find a better place to post this.
I have installed a brand new Ubuntu 8.04 Hardy Heron on my computer and decided to switch everything under Aptitude instead of Synaptic/Apt-get.

While trying to mark as automatically installed every possible installed packages, I've found a cyclic dependency which is:

language-support-en -> openoffice.org-thesaurus-en-au -> language-support-writing-en -> language-support-en

There is maybe other cyclic dependency, but my questions are:
Is it normal to have cyclic dependency between packages or is it a mistake that should be send to the package maintainer ?
Has anybody try to switch everything under Aptitude by marking everything ?

See ya all

---

### Post by mcduck on 2008-07-01
That's absolutely normal. If you have 2 packages that both need the other one to be installed as well to work, they of course should have the other package marked as dependency.

---

### Post by Frozsyn on 2008-07-01
It makes sense and I totaly agree, but this particular "language*" packages case looks strange to me. Anyway...

I have found that apt-get now include the commande autoremove that do the same thing as aptitude remove, so I don't know if it is useful to switch to aptitude anymore. I have to test more to see...

---

### Post by VMC on 2008-07-01
I've wondered why some people prefer using Aptitude over apt-get. I find Aptitude confusing, and don't understand the benefits.

---

### Post by mcduck on 2008-07-02
> **VMC said:**
> I've wondered why some people prefer using Aptitude over apt-get. I find Aptitude confusing, and don't understand the benefits.

There used to be some benefits, mainly the fact that aptitude was able to automatically uninstall packages installed as dependencies. But now apt-get can do that as well, so it's true that there isn't any real benefits over apt-get nay more.

Althogh Aptitude has a nice ncurses-based user interface if you like using those..

---

### Post by Frozsyn on 2008-07-02
> **VMC said:**
> I've wondered why some people prefer using Aptitude over apt-get. I find Aptitude confusing, and don't understand the benefits.
I've found a nice post that explain some reasons to prefer Aptitude over apt. Reading this article, you can see that sometimes, it's not just functionnalities that matter, but also things around it (ease of use, organisation, result readabitlity, ...):

[http://pthree.org/2007/08/12/aptitude-vs-apt-get/](http://pthree.org/2007/08/12/aptitude-vs-apt-get/)

---

### Post by sephirothrr on 2008-07-31
This is somewhat related - I have a laptop, and I need build-essential to install the madwifi drivers. Since I have no way of accessing the internet (no ethernet, etc) without wifi, I have taken the task of installing all the dependencies by hand. However, there are two packages that depend on each other. How do I install them?
The two packages in question are libstdc++6-4.2-dev and g++-4.2

---

### Post by Frozsyn on 2008-08-01
There should be no problem. If one package A depends on another B, and you ask for the installation of A, then the installation of B is automaticaly done. Am I missing something ?

---

### Post by mcduck on 2008-08-01
> **sephirothrr said:**
> This is somewhat related - I have a laptop, and I need build-essential to install the madwifi drivers. Since I have no way of accessing the internet (no ethernet, etc) without wifi, I have taken the task of installing all the dependencies by hand. However, there are two packages that depend on each other. How do I install them?
The two packages in question are libstdc++6-4.2-dev and g++-4.2

You can install many packages at the same time.
```
sudo dpkg -i package1.deb package2.deb
```

or install all packages in the current directory:
```
sudo dpkg -i *.deb
```

---

### Post by mcduck on 2008-08-01
> **Frozsyn said:**
> There should be no problem. If one package A depends on another B, and you ask for the installation of A, then the installation of B is automaticaly done. Am I missing something ?

Only if the packages are installed from the repositories. If they are downloaded by hand the package manager has no way of finding out where to find the other package.. (unless it either finds suitable package from the repositories, or you install the packages at the same time eith the commands in my previous post)

---

