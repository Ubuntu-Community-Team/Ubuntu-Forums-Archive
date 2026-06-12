---
title: "[installing] Torsmo"
date: 2004-11-29
forum: General Help
---

### Post by dewy on 2004-11-29
Hellow fellow ubuntuians, today is my first day using ubuntu and it is my first day on linux for at least 3 months, before I went back to the dark side for a small amount of time I was running Fedora Core 1 with a pretty well modded GUI running OpenBox, PyPanel and **Torsmo**. I decided I'd like to get torsmo running again and went to serch the apt-get respritories and came up with out luck (apt-cache search tormso). I then started to google for a .deb and found one on the debain web site and after trying to run it I noticed tehre was no program installed to handle it, I then went to google again and found out that Ubuntu sohuld not use Debian .debs so I finally decided to compile it. I downlaoded the source tarball and went on my way the first time I tried I got an error stating there was no C compiler, I then installed gcc (apt-get install gcc) this install gcc and gcc-3.1 (iirc) and I retired ./configure, I am now presented with this:
```
checking for X...
Sorry, X is very much needed
``` 
But what has me beat is I am trying to compile it from X, I have open a Xterm terminal in my Gnome Session. Could someone please help me out, I would love to get torsmo back up and running but if it is just basically imposible could some one please suggest an alternative, gDesklets is not an alternative tho)

**Link:** [Torsmo Homepage](http://torsmo.sourceforge.net/)

---

### Post by randy on 2004-11-30
It's probably checking for an X Development library that you have installed.  What one  it's checking for is tough to tell from what you posted.

---

### Post by WW on 2004-11-30
I'm not sure if this will help, but try installing **xlibs-static-dev**.  By the way, you can get most of the gcc tools that you need in one shot by installing **build-essential**.
```
sudo apt-get install build-essential
sudo apt-get install xlibs-static-dev
```

---

### Post by tom on 2004-12-01
I had the same problem. Installing **xlibs-static-dev** helped.

---

### Post by az on 2004-12-01
To add 2 cents, you are probably safer using a broader package like xlibs-dev.

The same goes for things like gtk, libqt, etc...

Just do a synaptic package search of the library name, and install the -dev package that seems to be the most basic.

---

### Post by mjrmua on 2005-06-21
I installed torsmo from the debian package here:
[http://packages.debian.org/unstable/x11/torsmo](http://packages.debian.org/unstable/x11/torsmo)

with 

dpkg --ignore-depends=libfontconfig1 -i torsmo_0.18-5_i386.deb

to stop it complaining about libfontconfig dependancies
seems to work ok.

---

