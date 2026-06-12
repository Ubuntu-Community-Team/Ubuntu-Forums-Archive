---
title: "kiba-dock(were did i go wrong)"
date: 2007-02-02
forum: General Help
---

### Post by STREETURCHINE on 2007-02-02
i installed kiba-dock by doing this.

      ```
sudo aptitude remove automake1.4 sudo aptitude install cvs automake1.9 build-essential cvs libpango1.0-dev libgtk2.0-dev libgconf2-dev libglitz-glx-dev librsvg2-dev checkinstall libglade2-dev libgtop2-dev

```

       ```
cvs -d:pserver:anonymous@metascape.afraid.org:/cvsroot co kiba-dock
```

       ```
cd kiba-dock ./autogen.sh make make install-schemas sudo checkinstall

```

      then to run i typed kiba-dock into terminal
 but i then got ,no such command found..

all the files seem to be there.
it could be that i missed a step
so any help would be great thank you..

---

### Post by russo.mic on 2007-02-03
try:

"make"

then:

"sudo make install"

in the kiba directory.  Worked for me!

Russo

---

### Post by STREETURCHINE on 2007-02-03
rex@rex-desktop:~$ cd kiba-dock ./autogen.sh make make install-schemas sudo checkinstall
rex@rex-desktop:~/kiba-dock$ make
make: *** No targets specified and no makefile found.  Stop.
rex@rex-desktop:~/kiba-dock$ 




thanks that did not work for me

---

### Post by sean222 on 2007-02-03
Ugh...I think you need to separate that line!! haha

```
sudo aptitude remove automake1.4
```

```
sudo aptitude install cvs automake1.9 build-essential cvs libpango1.0-dev libgtk2.0-dev libgconf2-dev libglitz-glx-dev librsvg2-dev checkinstall libglade2-dev libgtop2-dev
```

```
cvs -d:pserver:anonymous@metascape.afraid.org:/cvsroot co kiba-dock
```

```
cd kiba-dock
```

```
./autogen.sh
```

```
make
```

```
make install-schemas
```

```
sudo checkinstall
```

On the last step just put kibadock or whatever as the name and 0.1 or a number for the version number.

---

### Post by STREETURCHINE on 2007-02-03
sorry but i did most of it seperate,but i get the same result as i did the outher way.

thanks for your help

---

### Post by sean222 on 2007-02-03
I'm kinda new so I'm not sure :( Try deleting the kiba directory and try again from the beginning.

sudo rm -r /home/rex/kiba-dock

---

### Post by STREETURCHINE on 2007-02-03
thanks i just removed it i thought i may have to do that:)

---

### Post by sean222 on 2007-02-03
So does it work now? Those steps worked for me. Kiba-dock is pretty buggy by the way...for me at least.

---

### Post by STREETURCHINE on 2007-02-03
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Setting up graphviz-cairo (2.8-2) ...
/var/lib/dpkg/info/graphviz-cairo.postinst: 11: dot: not found
dpkg: error processing graphviz-cairo (--configure):
 subprocess post-installation script returned error exit status 127
Errors were encountered while processing:
 graphviz-cairo
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up graphviz-cairo (2.8-2) ...
/var/lib/dpkg/info/graphviz-cairo.postinst: 11: dot: not found
dpkg: error processing graphviz-cairo (--configure):
 subprocess post-installation script returned error exit status 127
Errors were encountered while processing:
 graphviz-cairo
rex@rex-desktop:~$ 


i keep getting errors now,may give up on it soon..lol:)

---

### Post by yigal.weinstein on 2007-02-03
To build kiba-dock you do not need graphviz-cairo.  Just 
aptitude purge graphviz-cairo , i.e. remove it and start over - if you have the patience. :)

I don't really like kiba-dock on my old machine - it eats up a lot of cpu/gpu and seams to slow my machine down some - but to each there own. :)

---

### Post by STREETURCHINE on 2007-02-03
oh i have plenty of patience,i have been trying to get kiba-dock working for 2 weeks now,i have installed and uninstalled it so many times,now i get this problem

rex@rex-desktop:~/kiba-dock$ ./autogen.sh
autoreconf: Entering directory `.'
autoreconf: configure.in: not using Gettext
autoreconf: running: aclocal 
/usr/share/aclocal/libmcrypt.m4:17: warning: underquoted definition of AM_PATH_LIBMCRYPT
  run info '(automake)Extending aclocal'
  or see [http://sources.redhat.com/automake/automake.html#Extending-aclocal](http://sources.redhat.com/automake/automake.html#Extending-aclocal)
autoreconf: configure.in: tracing
autoreconf: configure.in: creating directory config
autoreconf: configure.in: not using Libtool
autoreconf: running: /usr/bin/autoconf
configure.in:30: error: possibly undefined macro: AC_PROG_LIBTOOL
      If this token and others are legitimate, please use m4_pattern_allow.
      See the Autoconf documentation.
autoreconf: /usr/bin/autoconf failed with exit status: 1
rex@rex-desktop:~/kiba-dock$ make
make: *** No targets specified and no makefile found.  Stop.
rex@rex-desktop:~/kiba-dock$ 


i will eventually get it set up..:)

---

### Post by yigal.weinstein on 2007-02-03
I this is unfair because you have already told us you installed automake1.9 but please just for my interest 

```
aptitude search automake | grep '^i'
```

and give us the output :)

---

### Post by STREETURCHINE on 2007-02-03
dont have to worry to much about recources on this computer,
here is the result

rex@rex-desktop:~$ aptitude search automake | grep '^i'
i   automake1.9                     - A tool for generating GNU Standards-compli


sorry it took so long but absolute stinking hot here today went for a swim..

---

### Post by STREETURCHINE on 2007-02-03
ok so i seem to have succeeded so far but at the end it is asking me to write a description for the package.

Please write a description for the package.
End your description with an empty line or EOF.

so what do i write in here,

---

### Post by STREETURCHINE on 2007-02-03
still need some help..bump

---

### Post by yigal.weinstein on 2007-02-03
Right, ok when you checkinstall there are a number of fields you will want to change.   So
maker is:
0. root
change root to your email address or what ever you feel comfortable with

description:
1. a description of kiba-dock ( I think I got this from their website) is:
a fun dock program for Beryl. It works like an OS X dock, except it includes many more features. Kiba-dock has physics simulation, allowing icons to bounce around the screen and swing around like a rope, and other cool effects. Kiba-dock is run as a standalone program, but it depends on Beryl for its alpha-transparency. Currently, it can be compiled from source or installed from unofficial packages.

last but not least the version is a name, I can't remember what it was but you [COLOR="Sienna"]_must_[/COLOR] _change it to a number_ for checkinstall to work.  Change it to something like 1.

This should do it.

---

### Post by STREETURCHINE on 2007-02-03
thanks got it installed now i get a segmentation fault

rex@rex-desktop:~$ kiba-dock

(kiba-dock:10067): GConf-CRITICAL **: gconf_client_get_int: assertion `err == NULL || *err == NULL' failed
Segmentation fault (core dumped)
rex@rex-desktop:~$ kiba-dock

(kiba-dock:10097): GConf-CRITICAL **: gconf_client_get_int: assertion `err == NULL || *err == NULL' failed
Segmentation fault (core dumped)
rex@rex-desktop:~$ 



any idea on how to sort this out..:)

---

### Post by hanzomon4 on 2007-02-03
Did you make install-schemas?

---

### Post by STREETURCHINE on 2007-02-04
yep it is working fine it just breaks if i try to change some settings,
can i move it or is it permanantly stuck at the bottom..:)

---

### Post by yigal.weinstein on 2007-02-04
Good job, bravo.  I don't use the thing its too unstable for my taste but I hope you enjoy it. ):P :)

---

### Post by STREETURCHINE on 2007-02-04
thanks for all your help,

---

