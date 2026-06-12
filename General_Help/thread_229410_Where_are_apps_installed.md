---
title: "Where are apps installed?"
date: 2006-08-04
forum: General Help
---

### Post by FooAtari on 2006-08-04
I'm sure this has been asked before but I can't find anything.

I have installed Wengophone, and want to have it run at startup, but I have no idea where it is installed.

If not prompted for a location where do apps get installed to?

While I am on the subject where do you folks install apps and packages when prompted for location.  At the moment I have created folder call Programs under Home/USERNAME/ and put things in there.

Thanks

---

### Post by HAARP on 2006-08-04
Open a terminal and type
```
which program
```
It'll tell you where 'program' is

---

### Post by Tomosaur on 2006-08-04
the likelihood is that you will be able to run it by simply typing 'wengaphone' into a terminal.

Alternatively, use the 'which' command, or take a look in /usr/bin/ which is where most programs will live.

---

### Post by ifokkema on 2006-08-04
> **FooAtari said:**
> While I am on the subject where do you folks install apps and packages when prompted for location.  At the moment I have created folder call Programs under Home/USERNAME/ and put things in there.
Are you compiling stuff? If you just apt-get install then the program will be installed in the place(s) specified in the package. Executables in /usr/bin/, /bin, /sbin or /usr/sbin, libraries in /lib, /var/lib, /usr/lib, etc, etc.

If you're compiling your own stuff, you can put those files wherever you want. But when you sudo make install, I don't think there's a good way of tracking all files down that belong to the program.

---

### Post by Riverside on 2006-08-04
> **FooAtari said:**
> I have installed Wengophone, and want to have it run at startup, but I have no idea where it is installed.

If not prompted for a location where do apps get installed to?Wherever the package maintainer has configured the package to install the package's executable(s).  It can vary.

To view a list of all files installed by any particular installed package, use (for example):

```
anthony@catfish:~$ dpkg -L ipcalc
/.
/usr
/usr/bin
/usr/bin/ipcalc
/usr/share
/usr/share/doc
/usr/share/doc/ipcalc
/usr/share/doc/ipcalc/contributors
/usr/share/doc/ipcalc/README
/usr/share/doc/ipcalc/copyright
/usr/share/doc/ipcalc/changelog.Debian.gz
/usr/share/man
/usr/share/man/man1
/usr/share/man/man1/ipcalc.1.gz
/usr/share/man/man1/ipcalc_cgi.1.gz
/usr/share/images
/usr/share/images/ipcalc
/usr/share/images/ipcalc/ipcalc.gif
/usr/share/images/ipcalc/ipcalculator.png
/usr/lib
/usr/lib/cgi-bin
/usr/lib/cgi-bin/ipcalc
```

---

### Post by FooAtari on 2006-08-04
Thanks folks

@ifokkema. I mean when you install something you have downloaded from a site.  For example when I installed Mercury it hasked where I would prefer to install it.

Just wondered if there was a recomended or common location.  Or do you just use the default?

---

### Post by ifokkema on 2006-08-04
> **FooAtari said:**
> @ifokkema. I mean when you install something you have downloaded from a site.  For example when I installed Mercury it hasked where I would prefer to install it.

Just wondered if there was a recomended or common location.  Or do you just use the default?
There are too many software packages called Mercury, so I'm not sure which one you mean, but if it's small and can be contained in one directory, I would install it in something similar you have: /home/username/progs or so :)

---

### Post by FooAtari on 2006-08-05
It was Mercury Messenger :)

---

