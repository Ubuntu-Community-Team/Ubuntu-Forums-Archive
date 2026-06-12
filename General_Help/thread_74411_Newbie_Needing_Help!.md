---
title: "Newbie Needing Help!"
date: 2005-10-11
forum: General Help
---

### Post by Hereje on 2005-10-11
Hi!
Well this is my first tim posting here, I've actually installed Ubuntu Hoary in my PC and I've worked really hard on understanding the very complex world of Linux with lots of learnings but with a LOT of dissapointings...

This time problem is this, I don't have a broadband internet connection at home, but I'm using Ubuntu well there, In my University there is a bb connection so I use it for downloading everything Ubuntu requests me.

I have installed XMMS and BMP, they work fine, but I wanted to have something that I had on winamp: a Pitch control. So i looked for it and found SCIZZOR, downloaded it and tried to install it but couldn't, don't know how to install a package which doesn't have the .deb extension, Scizzor comes in a tar.gz file and really don't know what to do with this.

Please Help Me!!!

---

### Post by invalid on 2005-10-11
Typically this is the case with tar.gz files

```
tar xvfz package.tar.gz
```
this will unpack the contents
```
cd newdirectory
./configure
```
usually there will be a configure script, to make sure you have everything you need
```
make
```
or
```
make install
```
to install the software.

Most times the file will include a README too. It would be best to look at this to make sure you are doing the right steps.
```
cat README
```

Cheers,
Cb

---

### Post by Moha on 2005-10-11
don't forget: make clean
:razz:

---

### Post by darkmatter on 2005-10-11
Also, make sureyou install build-essentials if you intend to compile anything. You won't be able to unless you have this package.

You may also need a few additional libraries, ./configure will inform you if anything is missing.

---

