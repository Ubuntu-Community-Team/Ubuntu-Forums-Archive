---
title: "&quot;make[1]: no: Command not found&quot;"
date: 2008-05-28
forum: General Help
---

### Post by GrapeSoda on 2008-05-28
Hey all,

I'm attempting to install bitswash on Ubuntu 8.04- I've checked, double-checked, and triple-checked the dependencies (there are four: Boost, libtorrent, OpenSSL, and WxWidgets), but when I try to "make" the file following ./configure

```
Making all in src
make[1]: Entering directory `/home/octavian/Desktop/bitswash-0.0.6/src'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/home/octavian/Desktop/bitswash-0.0.6/src'
Making all in locale
make[1]: Entering directory `/home/octavian/Desktop/bitswash-0.0.6/locale'
no -o de_DE/bitswash.mo de_DE.po
make[1]: no: Command not found
make[1]: *** [de_DE/bitswash.mo] Error 127
make[1]: Leaving directory `/home/octavian/Desktop/bitswash-0.0.6/locale'
make: *** [all-recursive] Error 1

```

I saw a couple of other posts suggesting I install **mono-gmcs** and I did so, but with no luck...any ideas on how I can make "no" a recognized command?

---

### Post by sizzam on 2008-05-28
I don't know the answer to this question, however I did notice that bitswash.org points Ubuntu users to [this page]("http://www.getdeb.net/app/Bitswash") for a DEB package to install:

I was able to install this DEB file by first installing the libboost dependencies it needs:
```
sudo apt-get install libboost-filesystem1.34.1 libboost-date-time1.34.1 libboost-thread1.34.1
```

and then installing the downloaded DEB file with this command:
```
sudo dpkg -i bitswash_0.0.6-1~getdeb1_i386.deb
```

**** Update** -  I see that if you just double-click on the DEB file to install it, it will automatically find and install the dependencies.

---

### Post by aysiu on 2008-05-28
Try GetDeb?
[http://www.getdeb.net/app/Bitswash](http://www.getdeb.net/app/Bitswash)

---

### Post by bodhi.zazen on 2008-05-28
sizzam: just a little FYI.

Lets say you have a package, foo , as a .deb, foo.deb

To install it from the command line :

```
sudo dpkg -i foo.deb
```

Then to install the dependencies :

```
sudo apt-get install -f
```

Yes, you can skip all this with the gui tools, so more a FYI.

---

### Post by GrapeSoda on 2008-05-28
I tried using the deb package, and it looked like it installed fine, but am now getting segmentation errors when I try to run the program (also, it seems to be having issues opening up the flag images?)

I know of several other programs that I can try to get the same effect as bitswash, but I'm still intrigued as to why "no" is an unknown command...

---

