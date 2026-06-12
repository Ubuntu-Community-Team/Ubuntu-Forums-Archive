---
title: "can't make a .tar.gz file"
date: 2007-05-08
forum: General Help
---

### Post by jvanoort05 on 2007-05-08
i just downloaded a .tar.gz file. i looked around the forum and found out how to compile it but when i get to the 'make' command it just sais

josh@UBUNTU-HP:~/Desktop/avant-window-navigator-0.1.1$ make
make: *** No targets specified and no makefile found.  Stop.

what am i doing wrong?

---

### Post by bashologist on 2007-05-08
Usually you would have to type "./configure; make; sudo make install", or something like that to compile a program. What does the "install", or "readme" file say? Look around for a text file. Make sure to install the "build-essential" package too.

---

### Post by jvanoort05 on 2007-05-08
Then readme file sais

avant-window-navigator	0.1.1

./autogen.sh --prefix=/usr && make && make install

enjoy!!

launch with avant-window-navigator OR Applications->Accessories->Avant Window Navigator

configure with avant-preferences OR System->Preferences(->More Preferences)->Avant Preferences

-Neil

---

### Post by public_void on 2007-05-08
Run that series of commands as one or do it in turn.
E.g.
```
./autogen.sh --prefix=/usr && make && sudo make install
```or
```
./autogen.sh --prefix=/usr
make
sudo make install
```The script autogen.sh will be run first with the argument --prefix=/usr, then make, and finally make install.
 
Edit, yeah sudo,  my mistake.

---

### Post by Karlos on 2007-05-08
that would be "sudo make install" but an even better way would be to use checkinstall ( [http://asic-linux.com.mx/~izto/checkinstall/](http://asic-linux.com.mx/~izto/checkinstall/) ) rather than make install... checkinstall will create a .deb for you which can then be controlled using synaptic and apt-get etc.
do 
```
sudo apt-get install checkinstall
```
then
```
man checkinstall
```
for more info

by the way once checkinstall has created a .deb for you it can be installed using
```
sudo dpkg -i *.deb
```

---

### Post by jvanoort05 on 2007-05-08
> **public_void said:**
> Run that series of commands as one or do it in turn.
E.g.
```
./autogen.sh --prefix=/usr && make && sudo make install
```or
```
./autogen.sh --prefix=/usr
make
sudo make install
```The script autogen.sh will be run first with the argument --prefix=/usr, then make, and finally make install.
 
Edit, yeah sudo,  my mistake.

i did the './autogen.sh --prefix=/usr' comand and it runs for a while and then is stops and says

```
Checking for forbidden M4 macros...
***Error***: some autoconf macros required to build avant-panel-menu
  were not found in your aclocal path, or some forbidden
  macros were found.  Perhaps you need to adjust your
  ACLOCAL_FLAGS?
```

---

### Post by jvanoort05 on 2007-05-08
can some one plz help me with this?

---

### Post by rainwalker on 2007-05-08
If you're trying to get Avant installed, check out [http://ubuntuforums.org/showthread.php?t=385981](http://ubuntuforums.org/showthread.php?t=385981)
If you follow those steps it should work fine.

---

