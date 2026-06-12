---
title: "Can't uninstall programs"
date: 2019-04-19
forum: General Help
---

### Post by lutty2029 on 2019-04-19
I had downloaded the steam launcher a while ago and decide to uninstall it, I click on the menu, do a right click on the app and choose the option to uninstall, but for some reason it says that it can't find the package for dpkg-query. I have managed to uninstall steam but the problem with dpkg ccontinues, any help?:-s

---

### Post by similar2 on 2019-04-20
Try using the following command in a terminal:

```
sudo dpkg --configure -a
```

I'd suggest installing the **synaptic** package once the issue is resolved (not installed by default):

```
sudo apt install synaptic
```

From the SynapticHowto:

> Synaptic is a graphical front-end to [apt]("http://www.debian.org/doc/user-manuals#apt-howto"),  the package management system in Ubuntu. It combines the  point-and-click simplicity of the graphical user interface with the  power of the *apt-get* command line tool. You can install,  remove, configure, or upgrade software packages, browse, sort and search  the list of available software packages, manage repositories, or  upgrade the whole system. You can queue up a number of actions before  you execute them. Synaptic will inform you about dependencies  (additional packages required by the software package you have chosen)  as well as conflicts with other packages that are already installed on  your system.

---

### Post by HermanAB on 2019-04-20
Note that uninstalling a program is a bit like trying to unscramble an egg.  It may work, or your machine may end up unbootable, or somewhere in between those extremes.  

Consequently, over the years, I have learned never to try to uninstall a program I did not write myself.  Instead, once every two or three years, I reinstall my machines from scratch.

---

