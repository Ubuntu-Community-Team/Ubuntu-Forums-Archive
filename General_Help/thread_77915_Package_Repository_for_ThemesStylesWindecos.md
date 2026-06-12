---
title: "Package Repository for Themes/Styles/Windecos?"
date: 2005-10-17
forum: General Help
---

### Post by jvoegele on 2005-10-17
I was just wondering if anyone knows of a package repository that provides Ubuntu-compatible packages for some common themes, styles, icon sets, window decorations, and the like, many examples of which can be found on kde-look.org.

I would like to install several different styles and window decorations, but I would prefer using the package manager to install them as opposed to compiling and installing them myself.  I'm fine with a Debian repository as long as the packages are compatible with Breezy.

Thanks!

---

### Post by kayas80 on 2005-10-17
[quote=jvoegele]I was just wondering if anyone knows of a package repository that provides Ubuntu-compatible packages for some common themes, styles, icon sets, window decorations, and the like, many examples of which can be found on kde-look.org.

I would like to install several different styles and window decorations, but I would prefer using the package manager to install them as opposed to compiling and installing them myself. I'm fine with a Debian repository as long as the packages are compatible with Breezy.

Thanks![/quote]

I'm afraid I can't help, but if you find anything please let me know!

---

### Post by tonysathre on 2005-10-18
i have used the kde repo for installing such things as docks, and icon sets but havent found anything for installing themes and window decorations

---

### Post by ykpaiha on 2005-10-18
easy to turn out  (a bit as a spy-job but it works)

1) create a folder 
mkdir /home/your-name/xxxxx(in fact whatever you want)

2)add a repo:
sudo gedit /etc/apt/sources.list
add this into it:
deb-src [http://mirror.pusling.com/debian/unstable](http://mirror.pusling.com/debian/unstable) ./

3)open this mirror in your browser and you will see a numerous kwin and others "k"andies
they are all debian ready and so easely tranferable into kubuntu
[http://mirror.pusling.com/debian/unstable](http://mirror.pusling.com/debian/unstable)

4)you need to install every thing to compile
build essential, kde and kdelib -dev, fakeroot, autoconf, automake, debhelper...

5)then in a console (install mc it's easier) go in your new created dir
and simply type:
sudo apt-get source -b "the package name you like -you have seen in mirror pulsing"
after 1 minute or 2 you will get in the root of your dir a brand new *.deb package you can install or manage the way you want it

easy and educating !

if you have troubles in the compile you will see the messages error willtell you witch package is missing, you will find it easely in synaptic (quite often it's some *-dev)

have fun and let me know if it's usable for you

thanks to pusling in kde-ook for his job!
[http://www.kde-look.org/content/show.php?content=29317](http://www.kde-look.org/content/show.php?content=29317)

---

### Post by jvoegele on 2005-10-19
[QUOTE=ykpaiha]easy to turn out  (a bit as a spy-job but it works)
(snip)
2)add a repo:
sudo gedit /etc/apt/sources.list
add this into it:
deb-src [http://mirror.pusling.com/debian/unstable](http://mirror.pusling.com/debian/unstable) ./

3)open this mirror in your browser and you will see a numerous kwin and others "k"andies
they are all debian ready and so easely tranferable into kubuntu
[http://mirror.pusling.com/debian/unstable](http://mirror.pusling.com/debian/unstable)

4)you need to install every thing to compile
build essential, kde and kdelib -dev, fakeroot, autoconf, automake, debhelper...

5)then in a console (install mc it's easier) go in your new created dir
and simply type:
sudo apt-get source -b "the package name you like -you have seen in mirror pulsing"
after 1 minute or 2 you will get in the root of your dir a brand new *.deb package you can install or manage the way you want it
(snip)
[http://www.kde-look.org/content/show.php?content=29317](http://www.kde-look.org/content/show.php?content=29317)[/QUOTE]

Thanks for the pointer ykpaiha.  However, I notice that in addition to the deb-src that you demonstrate above, there is also a straight deb (i.e. binary, precompiled) package repository at the same site.  Are you using the deb-src and compiling yourself because that is the only way that it will work with Ubuntu, or is it merely your preference to compile these things yourself?  I ask because I would prefer not to have to compile myself if it is not necessary, and would prefer to use the binary precompiled packages.

Thanks!

---

### Post by jvoegele on 2005-10-19
[QUOTE=jvoegele]Thanks for the pointer ykpaiha.  However, I notice that in addition to the deb-src that you demonstrate above, there is also a straight deb (i.e. binary, precompiled) package repository at the same site.  Are you using the deb-src and compiling yourself because that is the only way that it will work with Ubuntu, or is it merely your preference to compile these things yourself?  I ask because I would prefer not to have to compile myself if it is not necessary, and would prefer to use the binary precompiled packages.[/QUOTE]

To answer my own question, it appears that the binary packages are *not* compatible with Ubuntu, so using the the deb-src approach outlined by ykpaiha above is necessary.

Thanks again, ykpaiha, I've now got several shiny new styles and window decorations thanks to you!

---

### Post by ykpaiha on 2005-10-19
[QUOTE=jvoegele]Thanks for the pointer ykpaiha.  However, I notice that in addition to the deb-src that you demonstrate above, there is also a straight deb (i.e. binary, precompiled) package repository at the same site.  Are you using the deb-src and compiling yourself because that is the only way that it will work with Ubuntu, or is it merely your preference to compile these things yourself?  I ask because I would prefer not to have to compile myself if it is not necessary, and would prefer to use the binary precompiled packages.

Thanks![/QUOTE]


those deb are for plain debian and not for ubuntu 
I made a repository here is the thread specialy after this post with  fully compatible and recompiled for ubuntu.:
[http://www.ubuntuforums.org/showthread.php?t=78886](http://www.ubuntuforums.org/showthread.php?t=78886)
Just use it

Donot hesitate to send a request  (or thank) if any

---

### Post by shenmue on 2005-10-19
[QUOTE=ykpaiha]those deb are for plain debian and not for ubuntu 
I made a repository here is the thread specialy after this post with  fully compatible and recompiled for ubuntu.:
[http://www.ubuntuforums.org/showthread.php?t=78886](http://www.ubuntuforums.org/showthread.php?t=78886)
Just use it

Donot hesitate to send a request  (or thank) if any[/QUOTE]

Can I install them after upgrading to KDE 3.5 Beta?

---

