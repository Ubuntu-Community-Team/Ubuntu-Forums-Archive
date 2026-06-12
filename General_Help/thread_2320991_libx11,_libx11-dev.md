---
title: "libx11, libx11-dev"
date: 2016-04-19
forum: General Help
---

### Post by brian125 on 2016-04-19
I am brand new to this and the program i am trying to install says i need libx11[COLOR=#000000][FONT=verdana], [/FONT][/COLOR]libx11-dev & zlib[FONT=verdana], [/FONT]zlib-dev.  I am showing that they are installed in the application manager but when installing the program i get this

/usr/bin/ld: cannot find -lX11
/usr/bin/ld: cannot find -lz

Is this something that must be done via command line?
Thanks in advance.
-clueless

---

### Post by ajgreeny on 2016-04-19
Tell us in more detail what you are trying to install, and the program you are using to try and install those packages.

You talk of "application manager" but I am not sure what you mean by that; presumably the **ubuntu-software-center** or **gnome-software** which is set to replace USC.

USC is not the best when searching for libraries such as those when using its default settings, so you may be better served by using the command line ```
sudo apt-get install  libx11 libx11-dev zlib zlib-dev
``` or if you prefer a GUI application to do this, first install synaptic package manager, and use that to search for and install those packages and just about anything else from the repos.

In the past synaptic was the default GUI package manager for Ubuntu, and in my opinion has never been surpassed.  I still use it a lot and it is the first extra package that I now add to any of the *ubuntu family in which it is not installed by default.

---

### Post by brian125 on 2016-04-19
synaptic package manager worked. it compiled! now to get it to run....

---

### Post by ajgreeny on 2016-04-20
Great! Please mark as SOLVED from the Thread Tools menu at the top.

---

