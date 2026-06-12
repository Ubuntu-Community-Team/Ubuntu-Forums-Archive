---
title: "dbdesigner"
date: 2005-07-19
forum: General Help
---

### Post by wrc on 2005-07-19
Hi

I'm trying to get dbdesigner (for mySQL) to work on Hoary. I googled and found some advice at

wiki.splitbrain.org/dbdesigner. 

When I run ./startdbd I get

Symbolic links exist
Starting DBDesigner4 ...

and thats it - nothing else. I expect it has something to do with the kylix libraries.

The link  stating more kylix libs needed: [http://www.fabforce.net/forum/viewtopic.php?p=2710#2710](http://www.fabforce.net/forum/viewtopic.php?p=2710#2710) is dead.

I am aware that this program is under current development and will be offered as a mySQL tool under a different name. In the meantime while we wait for that to happen, I'd like to use DBDesigner.

Any guidance would be most appreciated.

---

### Post by danielti on 2005-10-19
I have the same problem.
Please Help!

---

### Post by h4ck on 2005-10-21
YEs i have SAme problem with DBdesigner help please!

---

### Post by h4ck on 2005-10-23
Hy i have found the solution for DBdesigner.

Kylix Libraries:

wget      [http://heanet.dl.sourceforge.net/sourceforge/kylixlibs/kylixlibs3-borqt_3.0-1_i386.deb](http://heanet.dl.sourceforge.net/sourceforge/kylixlibs/kylixlibs3-borqt_3.0-1_i386.deb)
dpkg -i kylixlibs3-borqt_3.0-1_i386.deb

Then make a symbolic link to the lib and do ldconfig:

cd /usr/lib
ln -s kylix3/libborqt-6.9-qt2.3.so
ldconfig

That is all and then just run the program

---

### Post by daniloeu on 2007-01-13
Is much more easy to install DBDesigner under wine...

Its come correctly, with all features working.

But, if you have problems with new windows appering under main window, please see my blog:
[http://www.danilocesar.com/blog/2007/01/13/dbdesigner-wine-e-janelas-que-nao-ganham-foco/](http://www.danilocesar.com/blog/2007/01/13/dbdesigner-wine-e-janelas-que-nao-ganham-foco/)

---

