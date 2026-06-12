---
title: "[SOLVED] help compiling Worker"
date: 2007-07-02
forum: General Help
---

### Post by Subban on 2007-07-02
I am trying to compile newest version of Worker on Feisty, it is available from [http://www.boomerangsworld.de/cms/worker/download?lang=en](http://www.boomerangsworld.de/cms/worker/download?lang=en)

during ./configure it comes to a halt at this message:


```
checking for X... no
configure: error: X Window libraries and headers not found!
*********************************************************************
* Check your X installation (many distributions have these files in *
* the ...devel-packages (e.g. xdevel)).                             *
*********************************************************************
```

I have looked in Synaptic but just can't see what I should install to correct the error, can anyone point me in the right direction.

---

### Post by bmorency on 2007-07-02
> **Subban said:**
> I am trying to compile newest version of Worker on Feisty, it is available from [http://www.boomerangsworld.de/cms/worker/download?lang=en](http://www.boomerangsworld.de/cms/worker/download?lang=en)

during ./configure it comes to a halt at this message:


```
checking for X... no
configure: error: X Window libraries and headers not found!
*********************************************************************
* Check your X installation (many distributions have these files in *
* the ...devel-packages (e.g. xdevel)).                             *
*********************************************************************
```

I have looked in Synaptic but just can't see what I should install to correct the error, can anyone point me in the right direction.

How about trying to install the package named libx11-dev? that will install a bunch of development packages that might be useful. hope that helps.

---

### Post by Subban on 2007-07-02
> **bmorency said:**
> How about trying to install the package named libx11-dev? that will install a bunch of development packages that might be useful. hope that helps.

No that didn't help, it still won't compile and stops at the same point and same message

---

### Post by bmorency on 2007-07-02
how about installing xserver-xorg-dev or xorg-dev? i think xorg-dev might be it. it installs more packages.

---

### Post by Subban on 2007-07-02
> **bmorency said:**
> how about installing xserver-xorg-dev or xorg-dev? i think xorg-dev might be it. it installs more packages.

Selected xorg-dev for install in synaptic and it installed xserver-xorg-dev which you also mentioned anyways.

Anyways, with those two installed it compiled just perfect. 

Thank you for your suggestions, I really wasn't sure which -dev packages I needed to get it working, so I appreciate your time and input :]

---

### Post by bmorency on 2007-07-02
no problem. sometimes it can be a pain figuring out which dev package is needed.

---

