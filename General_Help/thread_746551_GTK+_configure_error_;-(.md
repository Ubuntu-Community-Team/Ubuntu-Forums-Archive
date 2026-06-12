---
title: "GTK+ configure error ;-("
date: 2008-04-05
forum: General Help
---

### Post by razta on 2008-04-05
Hello,
Trying to install GTK+ 2.12.9 on ubuntu 7.10 however get the following error:

```
ryan@ryan-desktop:~/Desktop/gtk+-2.12.9$ ./configure
configure: error: cannot find sources (gdk/gdktypes.h) in . or ..

```

Im installing GTK+ just to get LIVES working. Any one know how I can fix this? Im brand new to linux. :(

Thanks in advance,
Ryan

---

### Post by ad_267 on 2008-04-05
GTK should be installed already, you probably need the development library if you are compiling LiVES. Instead of compiling things from source it's a lot easier to use the synaptic package manager to install software you want.

To install the gtk development library go to system - administration - synaptic package manager and search for libgtk2.0-dev and install this package.

---

### Post by ad_267 on 2008-04-05
Also, from the LiVES website:

> Ubuntu
Ubuntu users can install LiVES simply by clicking on: [http://www.getdeb.net/app.php?name=lives](http://www.getdeb.net/app.php?name=lives)
Thanks to Joao Pinto !

Most applications for Ubuntu and other debian based linux distributions are installed using debian packages. These have a .deb extension. You can double click on these in the file browser to open them with the package installer and install them. The synaptic package manager is used to install debian packages from repositories, but because LiVES is not in the Ubuntu repositories you can download the package from the above website.

---

### Post by razta on 2008-04-06
Thanks for your replys, I went with kdenlive which was easy to install and did what I wanted, ill install LIVES to see if its any better. Thanks again!install LIVES to see if its any better.

---

