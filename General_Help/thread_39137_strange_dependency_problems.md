---
title: "strange dependency problems"
date: 2005-06-03
forum: General Help
---

### Post by _MiniMe_ on 2005-06-03
hi, 

 I was trying to install two appz today: transcode & gnomebaker from the CVS repo at (see [http://www.ubuntulinux.org/wiki/GnomeBaker)](http://www.ubuntulinux.org/wiki/GnomeBaker)).

 with both I get similar problems. This is the output from dpkg trying to install gnomebaker (OK, it's german but translation follows  ;-) )

gnomebaker hängt ab von libc6 (>= 2.3.2.ds1-21); aber:
  Version von libc6 auf dem System ist 2.3.2.ds1-20ubuntu13.
 gnomebaker hängt ab von libvorbis0a (>= 1.1.0); aber:
  Version von libvorbis0a auf dem System ist 1.0.1-1.
 gnomebaker hängt ab von libvorbisfile3 (>= 1.1.0); aber:
  Version von libvorbisfile3 auf dem System ist 1.0.1-1.

It needs libc6 (>=2.3.2.ds1-21) but there's only 2.3.2.ds1-20ubuntu13 installed. Same with the other 2. 
The Problem is that I can't find newer Versions of those 3 files. I got the multiverse and universe repos in my source.lst and also the backport-mirrors. Searching on Google also didn't help.

The problem appears with gnomebakerCVS, transcode and gstreamer0.8-lame, which also needs newer version of libc6.

Dunno what to do now. Can anybody help?

---

### Post by _MiniMe_ on 2005-06-03
Ok, 

I solved the problem by putting a debian unstable repo into my sources.list:
deb [http://ftp.de.debian.org/debian/](http://ftp.de.debian.org/debian/) unstable main contrib non-free

But now I have a new problem. After the update of libc6 the system language changed partially to english. Not all, but (at least) all the GNOME-Appz. A part of the menu is still german. A weird mix...

does anyone know how to change the language back to german?

---

