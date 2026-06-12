---
title: "Amule compilation with gtk2?"
date: 2005-04-13
forum: General Help
---

### Post by negatory on 2005-04-13
I've been trying to compile amule 2.0rc8 from source but I can't make it work with gtk2.I can compile it fine with gtk1 but I can't seem to get the wxWidgets linked with gtk2.

At the end of the ./configure script it says:
```
 Libraries aMule will use to build:
                                       wxWidgets          2.4.2
                                       GTK                1.2.10
``` 
and in the info tab in Amule it says
```
This is aMule 2.0.0rc8 using wxGTK1 v2.4.2 (based on eMule)
``` 

I've tried to compile wxGTK with --enable-gtk2 but with no luck.
Anyone had any luck doing this?
Thanks
Pedro Carrico

---

### Post by Nano on 2005-04-13
[QUOTE=negatory]I've been trying to compile amule 2.0rc8 from source but I can't make it work with gtk2.I can compile it fine with gtk1 but I can't seem to get the wxWidgets linked with gtk2.

At the end of the ./configure script it says:
```
 Libraries aMule will use to build:
                                       wxWidgets          2.4.2
                                       GTK                1.2.10
``` 
I've tried to compile wxWidgets with --enable-gtk2 but with no luck.
Anyone had any luck doing this?
Thanks
Pedro Carrico[/QUOTE]
 Why don't you just... install the .deb?
In their site you can find the package with GTK2. However, I found a better version in rediris.es repos for sid.

---

### Post by negatory on 2005-04-13
I'm using ubuntu for amd64 and the version they've got on their site complains that it can't locate some libraries.
Thanks
Pedro Carrico

---

### Post by Nano on 2005-04-13
[QUOTE=negatory]I'm using ubuntu for amd64 and the version they've got on their site complains that it can't locate some libraries.
Thanks
Pedro Carrico[/QUOTE]
 Try then the ones in rediris.es:

deb [http://ftp.rediris.es/debian](http://ftp.rediris.es/debian) unstable main contrib non-free
deb [http://non-us.debian.org/debian-non-US](http://non-us.debian.org/debian-non-US) unstable/non-US main contrib non-free

---

### Post by idn on 2005-04-13
I managed to download amule from the ubuntu repositories on my AMD63 installation, looks ugly tho :(

---

### Post by Nano on 2005-04-14
[QUOTE=idn]I managed to download amule from the ubuntu repositories on my AMD63 installation, looks ugly tho :([/QUOTE]

Because it's not gtk2

---

### Post by jeremy on 2005-04-14
why not just get the amule 2.0rc8 deb from amule.org ?

---

### Post by Nano on 2005-04-14
[QUOTE=jeremy]why not just get the amule 2.0rc8 deb from amule.org ?[/QUOTE]
 As he says in the second reply, he needs a amd64 version.

---

### Post by negatory on 2005-04-14
I just can't get the .deb for amd64 and all I wan't to know is how can I compile amule with gtk2.I just can't seem to compile the widgets linked with gtk2  ](*,) 
I've compiled the wxWidgets and gtk2 seperatly with no luck....
Has anyone done this?
Thanks
Pedro Carrico

---

### Post by pinok on 2005-04-15
First install wxgtk 2.5.3 -dev (from synaptic), version 2.0.0rc8 uses gtk2 for sure, and it looks very nice then :). I compiled the newest version of cvs, it works just fine.
[http://www.hirnriss.net/files/cvs/aMule-CVS-20050415.tar.bz2](http://www.hirnriss.net/files/cvs/aMule-CVS-20050415.tar.bz2)

---

### Post by negatory on 2005-04-15
Thank you very much!
That worked!I knew I was missing something!Now I have a gtk2 amule  :-P 
Thanks once again!

Pedro Carrico

---

### Post by idn on 2005-04-15
[QUOTE=pinok]First install wxgtk 2.5.3 -dev (from synaptic), version 2.0.0rc8 uses gtk2 for sure, and it looks very nice then :). I compiled the newest version of cvs, it works just fine.
[http://www.hirnriss.net/files/cvs/aMule-CVS-20050415.tar.bz2](http://www.hirnriss.net/files/cvs/aMule-CVS-20050415.tar.bz2)[/QUOTE]
 

sweet, my amule now looks awesome! Thanks alot :)

---

