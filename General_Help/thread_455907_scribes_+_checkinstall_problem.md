---
title: "scribes + checkinstall problem"
date: 2007-05-27
forum: General Help
---

### Post by cisforcojo on 2007-05-27
Has anyone installed scribes (the latest 0.3.2.5) with checkinstall?
I have previously installed 0.3.2.4 as a .deb from getdeb.net but I've run into a fairly annoying error and am working with the developer on it. 

scribes is available as a .tar.gz from scribes.sf.net but I absolutely loathe installing .tar.gz with make install
It's so messy and difficult to remove! If you want to remove it, you have to keep the source on your computer to 'make uninstall' and even then I'm not sure how reliable that is. 

So I use checkinstall but I'm getting this error. Any help???

```
(Reading database ... 143420 files and directories currently installed.)
Unpacking scribes (from .../scribes_0.3.2.5-1_i386.deb) ...
dpkg: scribes: warning - conffile `etc/gconf' is not a plain file or symlink (=
`/etc/gconf')
dpkg: scribes: warning - conffile `etc/gconf/gconf.xml.defaults' is not a plain
file or symlink (= `/etc/gconf/gconf.xml.defaults')
dpkg: error processing /home/cojones/Desktop/scribes-0.3.2.5/scribes_0.3.2.5-1_i
386.deb (--install):
 trying to overwrite `/usr/lib/libgconf2-4/2/libgconfbackend- xml.so', which is a
lso in package libgconf2-4
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /home/cojones/Desktop/scribes- 0.3.2.5/scribes_0.3.2.5-1_i386.deb
```

EDIT: This error occurs at "Installing Debian file..."

---

### Post by TheWizzard on 2007-05-27
it looks like the problem occurs from the configuration. 
check the source code directory and look for text file with instructions.

---

### Post by cisforcojo on 2007-05-27
Firstly, nice avatar!

Second, the source code directory definitely does not suggest using 'checkinstall'

It recommends using 'make install' which I hate because it's so messy. The only way (that I know of) to uninstall a make install is 'make uninstall' and I'm not sure how reliable that is. That's one thing I LOVE about Ubuntu is the .debs. It makes everything so much cleaner. After a bunch of .tar.gz installs, you don't know WHAT you have on your computer and how to get rid of it. You don't know what you need and what you don't. .deb solves all of that. 

Long story short, the source recommends 'make install' which I specifically don't like. So I'm stuck with trying to figure out why 'checkinstall' won't work

---

### Post by TheWizzard on 2007-05-27
thjere are 3 steps when using checkinstall:
1) ./configure 
2) make
3) sudo checkinstall 

often you'll need to add some parameters in step 1. this can depend on your hardware. 
please look for installation instructions.

---

### Post by cisforcojo on 2007-05-27
Yeah I know. Those are the steps I took.

The official steps for Scribes are:

1. configure
2. make
3. make install 

I'm not sure a variation in the configure step is what's throwing it off but then again, I won't say no. It's a really standard INSTALL file for this kind of installation. The developer didnt' have any idea since he doesn't use checkinstall.

---

### Post by TheWizzard on 2007-05-27
as far as i can judge your problem, it doesn't have anything to do with checkinstall. 

according to the scribes readme file, the first command should be
```
	./configure --prefix=/usr
```

---

### Post by cisforcojo on 2007-05-27
huh... well I tried it and it still failed. ugh!

---

### Post by TheWizzard on 2007-05-27
mmm, i'm affraid i can't help you further at this moment. 
cheers

---

### Post by mssever on 2007-06-08
If you're still looking for a scribes package, I have a (slightly patched) .deb in [my repository]("http://severance.homelinux.org:8066/falcon/dists/main/") that might be enough different from the getdeb version. It's version 0.3.2.6. Upstream just released two new versions, so I hope to update soon.

---

