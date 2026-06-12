---
title: "Gimpshop .deb ??"
date: 2005-10-01
forum: General Help
---

### Post by dbee on 2005-10-01
Is there any gimpshop .deb out there for easy installation ???

Thanks

---

### Post by bored2k on 2005-10-01
Debian compiled: [http://mirror.suramya.com/redirect.php?id=3](http://mirror.suramya.com/redirect.php?id=3)

---

### Post by dbee on 2005-10-01
cool, thanks b2k

---

### Post by dbee on 2005-10-02
oops ...   I thought a .deb would install on my ubuntu system no problem 

instead I'm getting a glibc version error ???

anyone know what I have to do to install it ?

I've tried installing from source but I get a gtk error

---

### Post by codejunkie on 2005-10-02
[QUOTE=dbee]oops ...   I thought a .deb would install on my ubuntu system no problem 
instead I'm getting a glibc version error ???
anyone know what I have to do to install it ?
I've tried installing from source but I get a gtk error[/QUOTE]
it compiled and runs fine on my system all i did was 
```
sudo apt-get install build-essential checkinstall linux-headers- `uname -r`
```
```
sudo apt-get build-dep gimp
```
then i ran "./configure" "make" and then "sudo checkinstall".

---

### Post by dbee on 2005-10-02
Hi codejunkie,

Did that install gimp or did it install gimpshop on your system ??

cheers,

---

### Post by Blue1k on 2005-10-02
I made one for Hoary and it also works in Breezy. 

If you want it, PM me and I will give you the link to my webspace. :)

---

### Post by codejunkie on 2005-10-02
[QUOTE=dbee]Hi codejunkie,
Did that install gimp or did it install gimpshop on your system ??
cheers,[/QUOTE]
it installed gimpshop those commands i used just provide the dependicies needed to compile it, and the ones you mentioned you were missing like gtk you still have to download and extract the gimpshop sourcecode and compile it. first you have to run 
```
sudo apt-get install build-essential checkinstall linux-headers-`uname -r`
``` then ```
sudo apt-get build-dep gimp
``` then download and extract the gimpshop sourcecode cd into the gimpshop sourcecode dir and run ```
./configure
``` then ```
make
``` as a normal user and then do ```
sudo checkinstall
```this will install gimpshop and create a .deb package that you can use to reinstall later without having to recompile in the gimpshop sourcecode dir if you have any trouble let me know and i try and help you get it running.

---

