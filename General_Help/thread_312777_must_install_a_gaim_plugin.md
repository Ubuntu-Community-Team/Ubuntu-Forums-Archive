---
title: "must install a gaim plugin"
date: 2006-12-04
forum: General Help
---

### Post by leetrefz on 2006-12-04
I need to get the openq plugin working for gaim or my wife will force me to install windows on pain of coital boycott. 

I went to Sourceforge, downloaded "openq-0.3.2.tar.gz", and extracted it to  

home. That's as far as I know how to get.

---

### Post by pay on 2006-12-04
```
cd openq*
sudo aptitude install build-essential
./configure
make
sudo make install #or if you want a debian file use checkinstall
```That would compile the source code. It is possible to convert an rpm to debian format```
sudo aptitude install build-essential alien
wget http://downloads.sourceforge.net/openq/gaim-openq-0.3.2-1.2.0.rh9.i386.rpm?modtime=1111164595&big_mirror=0
alien -i gaim-openq-0.3.2-1.2.0.rh9.i386.rpm
```

---

### Post by endersshadow on 2006-12-05
OpenQ has been merged into the gaim source code...you should be able to go to Accounts>Add and then select QQ from the drop down.

---

### Post by leetrefz on 2006-12-05
I tried that first, and the QQ option isn't there for me. Why should it be different?!?! It says I'm on version 1:2.0.0*beta3.1-1ubuntu9, and says that's the latest one. 

Doesn't seem fair.

---

### Post by Johan! on 2006-12-05
Debuntu.org's repository contains a newer gaim version.

Add this to your sources.list:
```
## Debuntu.org 
deb http://repository.debuntu.org/ edgy multiverse
deb-src http://repository.debuntu.org/ edgy multiverse

```

[www.debuntu.org](www.debuntu.org)

---

### Post by endersshadow on 2006-12-05
> **leetrefz said:**
> I tried that first, and the QQ option isn't there for me. Why should it be different?!?! It says I'm on version 1:2.0.0*beta3.1-1ubuntu9, and says that's the latest one. 

Doesn't seem fair.

Oh, sorry, I compiled Beta5 from source and totally forgot that I had.

Follow the above instructions, or get it and compile it for yourself from [here](http://gaim.sourceforge.net/).

---

### Post by leetrefz on 2006-12-05
the debuntu rep did the job. thnx!

---

