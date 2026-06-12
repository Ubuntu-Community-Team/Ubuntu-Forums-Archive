---
title: "libmagick9-dev dependencies"
date: 2007-05-16
forum: General Help
---

### Post by zackr on 2007-05-16
I'm using Ubuntu Feisty, and I am trying to get RMagick working. So installed GraphicsMagick and Imagemagick, but I apparently still need libmagick9-dev...

Running apt-get provides the following error:

sudo apt-get install libmagick9-dev
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libmagick9-dev: Depends: libwmf-dev (>= 0.2.7-1) but it is not going to be installed
                  Depends: libfreetype6-dev but it is not going to be installed
E: Broken packages


I tried to download the source for these but really I had no idea what to do with it, plus they have dependencies of their own. Is there an easy way to add a repository to get those two packages???

Help please! :confused:

---

### Post by jtraub on 2007-05-17
It works fine for my Feisty.
Probably you should enable axtra repositories and make 
```
sudo aptitude update
```

And repeat installation again.

---

