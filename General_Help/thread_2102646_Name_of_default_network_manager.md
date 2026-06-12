---
title: "Name of default network manager?"
date: 2013-01-07
forum: General Help
---

### Post by giantjoebot on 2013-01-07
I just installed Ubuntu Server 12.04, and then installed LXDE on it.  I want to sudo apt-get install the default network manager, but I don't know what the name is.

I'm also not sure if there is a different one for LXDE than for gnome?  I really like the gnome one though.

If anyone can tell me the name of the network manager so I can apt-get install I would really appreciate it.

---

### Post by Cheesehead on 2013-01-07
```
$ apt-cache depends lubuntu-desktop | grep network
  Depends: network-manager-gnome

```

If you installed Lubuntu the ordinary way (by installing the lubuntu-desktop metapackage), then the package you seek is network-manager-gnome...but it was already installed with Lubuntu.

If you installed LXDE some other way, then be aware that the package pulls in a few Gnome dependencies, too. I don't think it's too many, but your threshold for 'too many' may differ.

---

### Post by Bucky Ball on 2013-01-07
OP has installed lxde desktop environment, not lubuntu-desktop. 

[QUOTE=giantjoebot]I just installed Ubuntu Server 12.04, and then installed LXDE on it.
[/QUOTE]
You need:

```
sudo apt-get network-manager-gnome
```That may want to drag in quite a few dependencies. As it's a server you definitely do not want lubuntu-desktop. That will drag in everything; all apps and dependencies and you may as well have installed Lubuntu in the first place and added the server apps you need.

---

### Post by giantjoebot on 2013-01-07
After you guys replied I looked in Ubuntu software center, and saw it right there.  I don't know why I didn't see it before.  Thanks I really appreciate it

0 upgraded, 21 newly installed, 0 to remove and 93 not upgraded.
After this operation, 17.1 MB of additional disk space will be used

Its not working though, not sure why.  I'm probably going to give &#8211;no-install-recommends xubuntu-desktop a try since I'm having problems with audio as well.

Thanks for the help.  I really appreciate it.

---

### Post by Bucky Ball on 2013-01-08
Install just xfce4 if you only want the desktop environment. xubuntu-desktop will install the lot and again, you may as well have installed Xubuntu in the first place and added the server stuff ...

Try running these two commands before you try anything else as you have heaps to upgrade (although you're probably down the track by now):

```
sudo apt-get update
sudo apt-get upgrade
```

That will not upgrade you to the next release, just upgrades what you already have installed.

---

