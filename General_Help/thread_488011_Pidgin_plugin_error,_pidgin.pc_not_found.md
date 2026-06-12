---
title: "Pidgin plugin error, pidgin.pc not found"
date: 2007-06-29
forum: General Help
---

### Post by lairc on 2007-06-29
I just upgraded my GAIM to Pidgin for the single purpose of using the SIPE plugin from [http://sipe.sourceforge.net/](http://sipe.sourceforge.net/). I upgraded my Feisty installed GAIM to Pidgin by following this how-to:

[http://ubuntuforums.org/showthread.php?t=474071](http://ubuntuforums.org/showthread.php?t=474071)

Everything worked just fine. Pidgin worked perfectly. When I went to install SIPE, I started with the normal steps it chokes on the ./configure --prefix=/usr with the error:


checking pkg-config is at least version 0.9.0... yes
checking for libpurple... configure: error: Package requirements (pidgin >= 2.0.0) were not met:

No package 'pidgin' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables libpurple_CFLAGS
and libpurple_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.


Digging around through the log files I see that its looking for a pidgin.pc. I don't have that anywhere on my system.

Any ideas as to how I can get this thing to recognize that I have pidgin installed?

dpkg -l pidgin
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Installed/Config-files/Unpacked/Failed-config/Half-installed
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
ii  pidgin         2.0.2-1~getdeb multi-protocol instant messaging client

---

### Post by energiya on 2007-06-30
open a terminal, go to the SIPE directory:
```

make clean
export PKG_CONFIG_PATH=/usr/local/lib/pkgconfig:/usr/lib/pkgconfig
./configure --prefix=/usr

```
and then the rest (I think make && make install). I also think --prefix=/usr is speciffic to Slackware based systems? I'm not sure, but i don't think it matters in this case.

---

### Post by lairc on 2007-07-02
Still get the same error:
```
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for libpurple... configure: error: Package requirements (pidgin >= 2.0.0) were not met:

No package 'pidgin' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables libpurple_CFLAGS
and libpurple_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.


```


I looked into the PKG_CONFIG_PATH you suggested, I don't even have a pkgconfig in /usr/local/lib. It only contains:
```
$ ls /usr/local/lib/
python2.4  python2.5

```

---

### Post by energiya on 2007-07-02
Ok then. Try it in the following order:
1)post the output of ```
echo $PKG_CONFIG_PATH
```. If it's empty try again opening a terminal, and copy/paste and ENTER key
```

PKG_CONFIG_PATH=/usr/local/lib/pkgconfig:/usr/lib/pkgconfig

```
and then ./configure and the rest. If this doesn't work, go to 2

2) find "pidgin.pc"; you can do this from GUI or from the terminal. If you choose the last, the best way is
```

sudo updatedb
locate pidgin.pc

```
Note: updatedb could take a while.
If you find it, copy only the path to pidgin.pc and
```

PKG_CONFIG_PATH=$PKG_CONFIG_PATH":/path/without/the/last"/"

```
and try again to compile. If you can't find "pidgin.pc" or if this doesn't work, go to 3

3) before ./configure type in the terminal
```
libpurple_LIBS=/usr/lib
``` or where libpurple.so is. If this doesn't work... I don't know...

---

### Post by Jamie Jackson on 2007-08-22
I was in the same boat. I've got SIPE now, but am still waiting for it to support TLS. 

[Here's]("http://ubuntuforums.org/showpost.php?p=3235359&postcount=3") the easy way to install.

---

### Post by TreeFinger on 2007-12-14
Sorry for bringin back an old thread but I am having a similar problem. I just upgraded to 7.10 and installed pidgin. I'd like to install the plugin that shows what song is playing in rhythmbox inside my info.

```

checking for pidgin... configure: error: Package requirements (pidgin >= 2.0.0) were not met:

No package 'pidgin' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables pidgin_CFLAGS
and pidgin_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

```

---

### Post by TreeFinger on 2007-12-14
how do i make pidgin-rhythmbox-2.0 folder to make a so file I can put into the 
```

/usr/lib/pidgin

```

dir??

thats where all the plugins seem to be. they all are .so files.

there is also the dir..
```

/usr/lib/purple-2

```

which I believe has something to do with pidgin.

Is this plug-in just not up-to-date?

---

### Post by TreeFinger on 2007-12-15
I got this to work finally. I had to install pidgin-dev from synaptic. I think that should solve the OP's problems.. Here is a link to the HOW-TO on ubuntu forums..

[http://ubuntuforums.org/showthread.php?p=3958523#post3958523](http://ubuntuforums.org/showthread.php?p=3958523#post3958523)

---

### Post by midtown on 2007-12-21
Yes, the above guide worked, thanks. The trick was just installing pidgin-dev.

---

