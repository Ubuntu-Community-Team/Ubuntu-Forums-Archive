---
title: "Installing Opera"
date: 2007-05-16
forum: General Help
---

### Post by lukemack on 2007-05-16
Hi,

I am getting the following error when trying to install Opera on Ubuntu Server 6.10:

opera:
  Depends: libc6 (>=2.5-0ubuntu1) but 2.4-1ubuntu12.3 is to be installed
  Depends: libgcc1 (>=1:4.1.2) but 1:4.1.1-13ubuntu5 is to be installed
  Depends: libqt3-mt (>=3:3.3.8really3.3.7) but 3:3.3.6-3ubuntu3 is to be installed
  Depends: libstdc++6 (>=4.1.2) but 4.1.1-13ubuntu5 is to be installed

This error occurs using sudo apt-get or the syntapic package manager. I have also tried add/remove programs which states that I should use advanced mode i.e synaptic.

Does anyone know how I can resolve this? I have all the main repositories enabled in Synaptic preferences. Do I require an additional third-party repository?

I realise Opera is not a popular browser but I require it for client testing.

thanks,

lukemack.

---

### Post by DracoPsycho on 2007-05-16
Best possible action is to install mentioned packages ;)

---

### Post by lukemack on 2007-05-16
thanks - so I should install the later versions on the left of those lines before attempting to install opera? when it says 'is to be installed', does it mean that the opera package wants to install those?

---

### Post by yatt on 2007-05-16
You could try dpkg -if <packagename>

---

### Post by loathsome on 2007-05-16
Run something like this in bash;
```
sudo apt-get install libc6 && sudo apt-get install libgcc1 && sudo apt-get install libqt3-mt && sudo apt-get install libstdc++6
```

:)

And make sure your repositories are up to date;
```
sudo apt-get update
```

---

### Post by kerry_s on 2007-05-16
Yes it should pull in all the dependencys. Here's the repo i use to install opera and keep it up to date.->

deb [http://deb.opera.com/opera/](http://deb.opera.com/opera/) unstable non-free 

Key->

gpg --keyserver subkeys.pgp.net --recv-key 033431536A423791
sudo gpg --armor --export 033431536A423791| sudo apt-key add -

---

### Post by lukemack on 2007-05-16
thanks guys - I will give all that a try.

---

### Post by zvacet on 2007-05-16
[http://www.opera.com/download/]("http://www.opera.com/download/")

---

