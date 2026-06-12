---
title: "Aptik installation 19.04"
date: 2019-04-30
forum: General Help
---

### Post by habana on 2019-04-30
Prior to installing 19.04 I installed Aptik in 18.10 as follows:
```
sudo add-apt-repository -y ppa:teejee2008/ppa
sudo apt-get update
sudo apt-get install aptik aptik-gtk
```

Aptik installed OK and I backed up all my settings etc

After a clean install of 19.04 I tried to install Aptik repeating the above. The result was
```
sudo apt-get install aptik aptik-gtk
[sudo] password for bill: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package aptik
E: Unable to locate package aptik-gtk

```

So I thought I would try a deb. [http://ppa.launchpad.net/teejee2008/ppa/ubuntu/pool/main/a/aptik/](http://ppa.launchpad.net/teejee2008/ppa/ubuntu/pool/main/a/aptik/) lists debs for various ubuntu versions but not for 19.04 for which a tar.xz file is offered. This contains a number of files and folders but the readme file does not cover installation.

How do I proceed? And why can I not install from the PPA as before?

---

### Post by dino99 on 2019-04-30
reactivate your previous ppa version, it should work

---

### Post by habana on 2019-05-01
Thanks but it's gone: I did a clean install.

---

