---
title: "xbox game manager"
date: 2005-08-15
forum: General Help
---

### Post by f76 on 2005-08-15
hi all!

 I am trying to install xbgm -xbox game manager, it requires mono.. I think i have got that and now it wants gtk-sharp2 but i can only find gtk-sharp wherever I look i tried installing gtk-sharp bu i still get:
> the following packages have dependencies that cant be resoved(?):
  xbgmsharp: depends: gtk-sharp2 but it cant be installed
E: Broken package
 . 

where can i find gtk-sharp2 and is it safe for hoary?

thanks!

---

### Post by DJ_Max on 2005-08-15
Could you post your /etc/apt/sources.list

---

### Post by f76 on 2005-08-15
yes sir :
> deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary universe main restricted multiverse
 deb-src [http://se.archive.ubuntu.com/ubuntu](http://se.archive.ubuntu.com/ubuntu) hoary universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted

# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
 deb [http://orniere-du-globe.net/debian](http://orniere-du-globe.net/debian) ./
deb-src [http://orniere-du-globe.net/debian](http://orniere-du-globe.net/debian) ./

deb [http://kubuntu.org/hoary-kde341](http://kubuntu.org/hoary-kde341) hoary-updates main

deb [http://xbgm.sourceforge.net/debian](http://xbgm.sourceforge.net/debian) unstable/
deb-src [http://xbgm.sourceforge.net/debian](http://xbgm.sourceforge.net/debian) unstable/


---

### Post by f76 on 2005-09-04
I got help on Ubuntu-chat...

I just added > deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports main universe multiverse restricted
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras main universe multiverse restricted 
to the sources.list and then installed gtk-sharp2

---

