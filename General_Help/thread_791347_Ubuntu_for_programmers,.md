---
title: "Ubuntu for programmers,"
date: 2008-05-12
forum: General Help
---

### Post by davbren on 2008-05-12
Hey, a mate of mine would like Ubuntu to start programming in C but doesn't have an internet connection, how could he get the tools to program without a connection...?

---

### Post by ad_267 on 2008-05-12
You could download the packages and give them to him. If you have them installed they may be in /var/cache/apt/archives or you can download them from [http://packages.ubuntu.com/](http://packages.ubuntu.com/)

The only problem with this is that you can't automatically download any unmet dependencies. If you download a package you can open it with the package installer and see what dependencies are unmet and then download them too.

There is probably a better way than this though but I don't know it.

You could also try the ubuntu dvd which may have more of the packages required.

---

### Post by hermes0710 on 2008-05-12
I suppose you can install the essential packages through the cd (sudo apt-get install build-essential) and then download the source package of an ide (like anjuta), build it and done!

---

### Post by Sef on 2008-05-12
Moved to General Help.

---

### Post by pedro_orange on 2008-05-12
The package build-essential used to be on the Gutsy installation CD.

I would imagine it's still on the Hardy CD (But I don't have my distro CD checked in my Sotware Sources so I can't check)

---

### Post by tacutu on 2008-05-12
aptoncd helps you create an offline repository with the software you want.

---

