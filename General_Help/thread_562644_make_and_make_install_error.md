---
title: "make and make install error"
date: 2007-09-29
forum: General Help
---

### Post by billyransier on 2007-09-29
when ever i do a make or make install i ALWAYS get this error
make: *** No targets specified and no makefile found.  Stop.

i dont know what the problem is. i am following a guide to install my remote with mythtv and i got the error....

here is the webpage that i am following if anyone wants to see it.

[http://www.mythtv.org/wiki/index.php/LIRC_on_Ubuntu_Edgy_Eft](http://www.mythtv.org/wiki/index.php/LIRC_on_Ubuntu_Edgy_Eft)

is ther somehting else i need to type instead of make or make install?

ANY AND ALL HELP IS APPRECIATED!!!!

---

### Post by tbroderick on 2007-09-29
Did you install the build-essential package?

---

### Post by billyransier on 2007-09-29
yeah i installed it i got through the ./configure steps too.
just incase you wanted to know here are the files in the directory.....

root@MountainDew:/usr/src/lirc-0.8.1# dir
acconfig.h    config.h.in       COPYING        ltmain.sh      setup.data
acinclude.m4  config.log        daemons        Makefile.am    setup-driver.sh
aclocal.m4    config.sub        data2setup.sh  Makefile.in    setup.sh
ANNOUNCE      configure         depcomp        missing        stamp-h.in
AUTHORS       configure.in      doc            mkinstalldirs  TODO
ChangeLog     configure.lineno  drivers        NEWS           tools
compile       configure.sh      INSTALL        README
config.guess  contrib           install-sh     remotes

---

### Post by billyransier on 2007-09-29
when you said the "Build Essential Package" i assume you were talking about:

Setup build environment

 apt-get install ncurses-dev lirc

---

### Post by billyransier on 2007-09-29
sorry, that was my fault, i guess i didnt do the configure right case i did it again and what do you know, It WORKED!!!

thanks for your help anyways though

Peace
-Billy

---

### Post by tbroderick on 2007-09-29
...

---

