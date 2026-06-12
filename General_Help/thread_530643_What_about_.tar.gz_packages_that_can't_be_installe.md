---
title: "What about .tar.gz packages that can't be installed through APT?"
date: 2007-08-20
forum: General Help
---

### Post by sdim on 2007-08-20
Many thanks to everyone who is helping us rookies with Ubuntu.
Indeed,a marvellous OS,but there are still problems understanding how to install things,like e.g. .tar.gz packages through APT.Is there a distinction between those which contain source and those which don't?
Please,help...I tried various help pages but there are still packages I can't install...

---

### Post by Happy_Man on 2007-08-20
If you want to install .tar.gz packages, you will have to do it manually. Download the file in question, extract to the desktop, and then open a terminal and type in these commands: ```
cd ~/Desktop/<name of folder>
./configure
make
sudo make install
``` 

For more tips, see here: [http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

---

### Post by rainwalker on 2007-08-20
> **Happy_Man said:**
> If you want to install .tar.gz packages, you will have to do it manually. Download the file in question, extract to the desktop, and then open a terminal and type in these commands: ```
cd ~/Desktop/<name of folder>
./configure
make
sudo make install
``` 

For more tips, see here: [http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

Couldn't they also be installed with GDebi?
Applications -> System Tools -> GDebi Package Installer

---

### Post by Happy_Man on 2007-08-20
> **rainwalker said:**
> Couldn't they also be installed with GDebi?
Applications -> System Tools -> GDebi Package Installer
Only if they are .deb form. Anything else, you will need to do it manually.

---

### Post by rainwalker on 2007-08-20
Oh, duh! 
Haha sorry, my mistake

---

### Post by sdim on 2007-08-20
Thank you both for the answers.
I'll try it.

---

### Post by bodhi.zazen on 2007-08-20
You might like to look at checkinstall

checkinstall replaces the final make install so,

./configure
make
sudo checkinstall

check install makes a .deb out of the source code , this makes it easier in the future, if it works (checkinstall sometimes fails).

a .deb is a binary package (it has been compiled) packaged according to packaging standards

[http://www.debian.org/doc/maint-guide/](http://www.debian.org/doc/maint-guide/)

[http://doc.ubuntu.com/ubuntu/packagingguide/C/](http://doc.ubuntu.com/ubuntu/packagingguide/C/)

==========

The tar is the source code. It is compiled (make && make install) into a binary.

HTH

---

### Post by sdim on 2007-08-20
Thank you very much for the help,but it's a bit too technical for me.
Hope Il'learn along the way.There seem to be various things falling into the same categories,so it may be too soon to learn after a week of using Ubuntu.

---

