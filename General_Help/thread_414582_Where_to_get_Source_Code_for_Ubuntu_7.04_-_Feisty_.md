---
title: "Where to get Source Code for Ubuntu 7.04 - Feisty Fawn?"
date: 2007-04-20
forum: General Help
---

### Post by TwistedLincoln on 2007-04-20
I'm in the process of downloading Ubuntu 7.04.  Looks good from everything I've read.

But where can I download the source code?  I don't see any source iso's on any of the mirrors, nor does it seem that I can order a source code CD from the Ubuntu shop.

I'd like to be able to redistribute Ubuntu 7.04, but want to fully comply with the GPL by providing the full corresponding source code.

Any assistance is greatly appreciated.

---

### Post by ubuntu27 on 2007-04-20
If things haven't change. The Source code is in the repositories.

Open the Terminal:

sudo apt-get build-dep nameofpackage

and

sudo apt-get source nameofpackage

example:

```
sudo apt-get build-deb epiphany-browser
```

```
sudo apt-get source epiphany-browser
```



You can also download the source using your favorite browser:

Just go to [http://packages.ubuntu.com/edgy/source/](http://packages.ubuntu.com/edgy/source/)

---

### Post by TwistedLincoln on 2007-04-20
Is there a command to retreive the source for ***_ALL_*** the packages in the distro?  

I need the full corresponding source code for everything on the installation CD in order to comply with the GPL.  Most distros have a source CD iso available for download that has everything you need.  

After many posts here and lots of searching, I found a source ISO for Edgy (6.10).  But it wasn't easy to find at all.  Canonical should really have a source ISO in an easy to locate place for each edition.  

In any case, does anyone know where I can get the full source for 7.04?

---

### Post by rai4shu2 on 2007-04-20
[http://cdimage.ubuntu.com/releases/feisty/release/source/](http://cdimage.ubuntu.com/releases/feisty/release/source/)

It may take a minute for the page to load.

---

### Post by cooldude95 on 2007-08-10
> **rai4shu2 said:**
> [http://cdimage.ubuntu.com/releases/feisty/release/source/](http://cdimage.ubuntu.com/releases/feisty/release/source/)

It may take a minute for the page to load.

THANK YOU THANK YOU THANK YOU THANK YOU THANK YOU!!!!!!!!!! :D :D :D :D :D :D :D :D

---

