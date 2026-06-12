---
title: "gmplayer problems :/"
date: 2004-12-16
forum: General Help
---

### Post by eedok on 2004-12-16
FIXED
Caused by having debian repo in my repo list and it was looking for sarge libraries rather than ubuntu ones.
----------------------



Well I can get mplayer-nogui to install, but trying to install mplayer-k7(I'm on a athlon XP) I get this:
```

mplayer-k7:
 Depends: mplayer-k6 but it is not going to be installed

```
so when I try to install mplayer-k6 I get this error message:
```

mplayer-k6:
  Depends: libartsc0 but 1.2.3-1 is to be installed
  Depends: libfribidi0 but 0.10.4-3 is to be installed
  Depends: libggi2 but 1:2.0.4-3 is to be installed
  Depends: libpng12-0 but 1.2.5.0-7ubuntu1 is to be installed
  Depends: libungif4g but 4.1.0b1-6 is to be installed

```
trying to install just the plain mplayer results in this:
```

mplayer:
  Depends: libggi2 but 1:2.0.4-3 is to be installed
  Depends: libpng10-0 but 1.0.15-6ubuntu1 is to be installed

```

Any way to actually get this installed?

---

### Post by liberal_tugboat on 2004-12-16
i downloaded the source code for mplayer and compiled it myself as per the instuctions  [HERE](http://ubuntuforums.org/showthread.php?t=94) 
I think this is a better way to go for mplayer, seems like many dont have success with the dpkg files.

---

### Post by Domecq on 2005-03-08
I found a simple solution in Synaptics that worked for me.

First of all, it's necessary to have the following repositories added and enabled in Synaptics:
Marillat
-----------
URI: [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/)
Distribution: testing (use unstable here if you are using hoary)
Section(s): main

and

Crimsun
------------
URI: [http://sh.nu/~crimsun/](http://sh.nu/~crimsun/)
Distribution: ./
Section(s): (leave blank)

Next step...

Just highlight the mlpayer package that you want to be installed (i.e. i386, i588... K6 etc.)

In Synaptics menu, go to "package", then "force version", then, in the new window, choose the version 1.0-pre6a-0.0 (sh.nu)

---

### Post by botinok6596 on 2007-05-15
Spam.

---

