---
title: "x libaries"
date: 2007-12-26
forum: General Help
---

### Post by Elena678 on 2007-12-26
hello, do someboddy know what are x libaries, and how i can install them, i have an aplication that needs them, but can't find them, my kubuntu instalation is only 3 days old, so it would be stage if i allready deleted it :S

greetings

---

### Post by jespdj on 2007-12-26
Give us some more details. What software are you trying to install that need those libraries? Can't you install it from the package manager (**adept** on Kubuntu)?

"X" most likely means the "X window system", which is the windowing system that KDE (and GNOME) is based on.

---

### Post by Elena678 on 2007-12-26
oh, sorry, will try to give more info, the package i would like to install is kooldock-0.4.7

I found it here: [http://www.kde-look.org/content/show.php/kooldock?content=50910](http://www.kde-look.org/content/show.php/kooldock?content=50910)

but when i install it it gives me the following result:
checking for X... configure: error: Can't find X libraries. Please check your installation and add the correct paths!

I hope this will help you with helping me :D

Thanks for the help

greetings

---

### Post by PeterJS on 2007-12-26
Does the deb file from KDE look work? It's always better to install from a deb for managing versions, uninstalling,etc.

Also the error message is a bit misleading, I can tell you right now that you already have the X libs installed, because you're running a graphical environment, what the error message actually means is it wants the X developer packages, in this case it was a particularly cryptic message and doesn't even give a decent hint as to what it's actually looking for.

The deb up on Kde look is version 0.4.6, and in the ubuntu repositories there is a deb for version 0.3.1

---

### Post by Elena678 on 2007-12-26
well, i installed the debian file, de kooldock-0.4.6. it was doing a lot when i pressed install, but after the install i can't find annything back :S

thanks for the help

greeings

---

### Post by PeterJS on 2007-12-26
If you open up synaptic and search for kooldock you should find it, if you right click on it and go to Properties > Installed Files, it will give you a complete listing of the files the package installed, you're looking for something in one of the bin folders, I'd guess /usr/bin/kooldock.

---

### Post by Elena678 on 2007-12-26
It is working, a bit a pitty it stay on the foreground of my windows, but it is working, thanks a lot for the help

greetings

---

