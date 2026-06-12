---
title: "APT problem dependencies for amule"
date: 2005-05-20
forum: General Help
---

### Post by geearf on 2005-05-20
Hello,

This is resolved, see the last post for my new problem, thanks !:)

i'd like to compile aMule, (i know i can get it on a .deb, but i'd like to compile it myself ;) ) but i need some GTK libs for that, but i cannot install them :(


The following packages have unmet dependencies:
  libgtk2.0-dev: Depends: libglib2.0-dev (>= 2.4.1-2) but it is not going to be installed
                 Depends: libpango1.0-dev (>= 1.5.1) but it is not going to be installed
                 Depends: libatk1.0-dev (>= 1.6.1-2) but it is not going to be installed
E: Broken packages

What can i do for that please ?
Thanks

---

### Post by ujay on 2005-05-20
I had a similar problem with another app.  I had to uncomment some lines in /etc/apt/sources.list, and then perform apt-get update, which got the required dependancies.  You may need to uncomment the univers and restricted source listings

---

### Post by geearf on 2005-05-20
Hello,

those are already uncommented in fact :(
I think my problem is that i have some 'too' new versions of the files i need, i need to downgrade it seems :(
But even with --reinstall -t hoary, i cannot.

It tells me it cannot downgrade !(

---

### Post by geearf on 2005-05-20
Well in fact it seems this did the trick : 
[http://packages.ubuntu.com/cgi-bin/download.pl?arch=i386&file=pool%2Fmain%2Fg%2Fglib2.0%2Flibglib2.0-0_2.6.3-1_i386.deb&md5sum=151b6c4d0a6a72d26c8557532eb5c67d&arch=i386&type=main](http://packages.ubuntu.com/cgi-bin/download.pl?arch=i386&file=pool%2Fmain%2Fg%2Fglib2.0%2Flibglib2.0-0_2.6.3-1_i386.deb&md5sum=151b6c4d0a6a72d26c8557532eb5c67d&arch=i386&type=main)

Strangely i could not find any of my repos holding this file.

---

### Post by geearf on 2005-05-21
My compile went very fine, but i still have a little problem,
when i start amule, it works with amule, but not with amule &.

And when i shutdown amule (can't do ctrl z), i can type anything, but i don't see what i am writing on the konsole used to type, any ideas on this ?

Thanks

---

