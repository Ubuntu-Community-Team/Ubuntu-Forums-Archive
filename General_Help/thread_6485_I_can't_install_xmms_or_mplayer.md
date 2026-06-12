---
title: "I can't install xmms or mplayer"
date: 2004-11-29
forum: General Help
---

### Post by Martin Georgiev on 2004-11-29
Hello everyone.

I'm a new to linux and even more new to ubuntu. I've been trying to install xmms and mplayer but:

root@ubuntu:/home/martin # sudo apt-get install xmms
Reading Package Lists... Done
Building Dependency Tree... Done
Package xmms is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package xmms has no installation candidate
root@ubuntu:/home/martin #

Any advises?

Thanks in advance

---

### Post by poofyhairguy on 2004-11-29
[QUOTE=Martin Georgiev]Hello everyone.

I'm a new to linux and even more new to ubuntu. I've been trying to install xmms and mplayer but:

root@ubuntu:/home/martin # sudo apt-get install xmms
Reading Package Lists... Done
Building Dependency Tree... Done
Package xmms is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package xmms has no installation candidate
root@ubuntu:/home/martin #

Any advises?

Thanks in advance[/QUOTE]


1. type this into a console

sudo gedit /etc/apt/sources.list 

2. delete whats in the doc

3. replace your list with mine here:


deb [ftp://ftp.belnet.be/packages/ubuntu/](ftp://ftp.belnet.be/packages/ubuntu/) warty main restricted  
deb-src [ftp://ftp.belnet.be/packages/ubuntu/](ftp://ftp.belnet.be/packages/ubuntu/) warty main restricted  

deb [ftp://ftp.belnet.be/packages/ubuntu/](ftp://ftp.belnet.be/packages/ubuntu/) warty universe multiverse  
deb-src [ftp://ftp.belnet.be/packages/ubuntu/](ftp://ftp.belnet.be/packages/ubuntu/) warty universe multiverse  

deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) warty-security main restricted 

deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) testing main 



4. put in console

sudo apt-get update

5. Then install at will. As a note, the xmms works fine for me, but the mplayer won't install. For media files I use xine, which installs fine and plays EVERYTHING. 

sudo apt-get install xine-ui

sudo apt-get install xmms

good luck. Hopefully a new repo will come soon just for non-legal Ubuntu files like Mplayer!

---

### Post by jiyuu0 on 2004-11-29
or...

Add-On Applications Section
[http://kitech.com.my/ubuntu/4.10/index.html](http://kitech.com.my/ubuntu/4.10/index.html)

---

### Post by Martin Georgiev on 2004-11-29
Thank you both! Thi was very helpful. I own you both a beer! I mean a beer for everyone as begginning  ;)

---

