---
title: "help needed to compile a program"
date: 2015-04-09
forum: General Help
---

### Post by jack0987 on 2015-04-09
Being a newbie is hard.

I am trying to compile a program for my linux 32 bit computer but am having great difficulties.

Could someone help step by step please.

Here is the link to the source code

[https://github.com/sgminer-dev/sgminer/releases](https://github.com/sgminer-dev/sgminer/releases)

I am doing version 5.1.1

I have downloaded it.
Extracted it to a directory on the desktop.
Opened the terminal.
Navigated to it's directory in the terminal.

What do I do now?

---

### Post by dino99 on 2015-04-09
[https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo)

---

### Post by jack0987 on 2015-04-09
This is what I have done so far following a tutorial:

sudo apt-get install autoconf opencl-headers libcurl4-openssl-dev libtool libncurses5-dev

cd /tmp

wget [https://github.com/sgminer-dev/sgminer/archive/5.1.1.tar.gz](https://github.com/sgminer-dev/sgminer/archive/5.1.1.tar.gz)

tar -xf 5.1.1.tar.gz

cd sgminer-5.1.1

-- Download ADL From [http://developer.amd.com/tools-and-sdks/graphics-development/display-library-adl-sdk/](http://developer.amd.com/tools-and-sdks/graphics-development/display-library-adl-sdk/)
-- Unzip and copy files from include/* to sgminers/ADL_SDK/ folder

libtoolize

Up to this point things seem to be ok. however now I need to run autoreconf -ivf and get an error

administrator@LS1 /tmp/sgminer-5.1.1 $ autoreconf -ivf
autoreconf: Entering directory `.'
autoreconf: configure.ac: not using Gettext
autoreconf: running: aclocal -I m4 --output=aclocal.m4t
Can't exec "aclocal": No such file or directory at /usr/share/autoconf/Autom4te/FileUtils.pm line 326.
autoreconf: failed to run aclocal: No such file or directory

It is looking for aclocal what ever that is.

---

### Post by Holger_Gehrke on 2015-04-09
aclocal is part of automake, which would have been installed if you had done as the link 9d9 posted suggests and installed the 'build-essentials' meta-package.

---

### Post by jack0987 on 2015-04-09
thanks so much for your reply.

I did do step one per 9d9 as I recall.

Is it possible that since I am working in the temp directory, it is not being picked up on the system path?

---

### Post by steeldriver on 2015-04-09
I don't recall 'automake' being a dependency of build-essential (although 'make' is) - try installing the 'automake' package explicitly

---

