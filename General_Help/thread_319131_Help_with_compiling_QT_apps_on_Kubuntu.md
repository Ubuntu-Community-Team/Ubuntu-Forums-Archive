---
title: "Help with compiling QT apps on Kubuntu"
date: 2006-12-15
forum: General Help
---

### Post by Bigglez on 2006-12-15
Hi, I'm on Kubuntu 6.06.
I want to compile a QT app which requires QT4 and I am just not sure which packages to install in order to do so.

1. I *have* installed build-essential
2. Here are some dumps of what I have tried-
```
unichr:$ sudo apt-get install libqt4-core libqt4-dev libqt4-gui qt4-dev-tools
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libqt4-dev: Depends: libxcursor-dev but it is not going to be installed
              Depends: xlibmesa-gl-dev but it is not installable or
                       libgl-dev
              Depends: libglu1-xorg-dev but it is not installable or
                       libglu1-mesa-dev but it is not going to be installed or
                       libglu-dev
E: Broken packages
```
Which is pretty typical of whatever I have tried :(
I'm kinda scared of starting to apt-get all those deps; I picture each one of them asking for others in this horrendous infinite tree of hell .... :twisted: 

Can anyone give me the low-down?

Donn.

---

### Post by Bigglez on 2006-12-16
bump - anyone?

---

### Post by der_joachim on 2006-12-16
Have you tried the following command?```
sudo apt-get build-dep <yourpackage>
```

---

### Post by Bigglez on 2006-12-17
Hi, don't know that one. What is <yourpackage> supposed to be?

---

### Post by Bigglez on 2006-12-17
These are the files that I want to compile. The INSTALL file says: qmake then make, but I can't seem to get QT4 dev stuff installed.

unichr:$ ls
charfield.cpp  LICENSE   unichart.cpp      unichart.menu  widgets.h
charfield.h    main.cpp  unichart.desktop  unichart.pro
INSTALL        Makefile  unichart.h        widgets.cpp

---

### Post by Bigglez on 2006-12-18
budda-budda-bump!

---

### Post by po0f on 2006-12-18
Bigglez,

```
[FONT="Courier New"]$ sudo aptitude install libqt4-dev[/FONT]
```

---

### Post by NeoChaosX on 2006-12-18
Bigglez: Mind showing us your /etc/apt/sources.list?

---

### Post by Bigglez on 2006-12-18
po0f = please see my OP.

NeoChaosX, here:

```
unichr:$ cat /etc/apt/sources.list

deb http://archive.ubuntu.com/ubuntu/ dapper main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ dapper main restricted universe multiverse

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu/ dapper-updates main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ dapper-updates main restricted universe multiverse

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
#deb http://za.archive.ubuntu.com/ubuntu/ dapper universe
#deb-src http://za.archive.ubuntu.com/ubuntu/ dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu dapper-security main restricted universe multiverse
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted universe multiverse

# deb cdrom:[Kubuntu 6.06 _Dapper Drake_ - Release i386 (20060531)]/ dapper main restricted

#Automatix
deb http://www.getautomatix.com/apt kubuntu main

#XGL/Xompiz
# deb http://xgl.compiz.info/ dapper main
# deb-src http://xgl.compiz.info/ dapper main
# deb http://www.beerorkid.com/compiz/ dapper main

## PLF REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb http://packages.freecontrib.org/plf dapper free non-free
deb-src http://packages.freecontrib.org/plf dapper free non-free                                                                                              
## CANONICAL COMMERCIAL REPOSITORY (Hosted on Canonical servers, not Ubuntu
## servers. RealPlayer10, Opera and more to come.)
deb http://archive.canonical.com/ubuntu dapper-commercial main

# wxPython APT repository at wxcommunity.com
deb http://wxpython.wxcommunity.com/apt/ubuntu/dapper /
deb-src http://wxpython.wxcommunity.com/apt/ubuntu/dapper /

#qcomic repo... gulp!
deb http://qcomicbook.horisone.com/ dapper main
deb-src http://qcomicbook.horisone.com/ dapper main

#Jahshaka
deb http://repo.jahshaka.org/ubuntu/dapper/ binary-i386/

```

Thanks for your help!

---

### Post by po0f on 2006-12-18
Bigglez,

Please re-read my command.  I said `aptitude`, not `apt-get`.  aptitude is a lot better at installing stuff than apt-get.

---

### Post by Bigglez on 2006-12-18
poOf - my apologies - aptitude is new to me too!

Well, I did as you said, and I am still confused. Now, it could be that QT4-dev is installed and working but the app I want to compile is just broken, or it could be .. other stuff.

Here is the result of the aptitude, there seems to be a problem and nothing was installed:
```
unichr:$ sudo aptitude install libqt4-dev
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
The following packages are BROKEN:
  libgl1-mesa-dev libglu1-mesa-dev libxfixes-dev
The following NEW packages will be automatically installed:
  libaudio-dev libexpat1-dev libfontconfig1-dev libfreetype6-dev
  libice-dev libjpeg62-dev liblcms1-dev libmng-dev libpng12-dev
  libqt4-core libqt4-gui libqt4-qt3support libqt4-sql libsm-dev libx11-dev
  libxau-dev libxcursor-dev libxdmcp-dev libxext-dev libxft-dev libxi-dev
  libxinerama-dev libxmu-dev libxmu-headers libxrandr-dev libxrender-dev
  libxt-dev mesa-common-dev pkg-config qt4-designer qt4-dev-tools qt4-doc
  qt4-qtconfig x-dev x11proto-core-dev x11proto-fixes-dev
  x11proto-input-dev x11proto-kb-dev x11proto-randr-dev
  x11proto-render-dev x11proto-xext-dev x11proto-xinerama-dev zlib1g-dev
The following NEW packages will be installed:
  libaudio-dev libexpat1-dev libfontconfig1-dev libfreetype6-dev
  libice-dev libjpeg62-dev liblcms1-dev libmng-dev libpng12-dev
  libqt4-core libqt4-dev libqt4-gui libqt4-qt3support libqt4-sql libsm-dev
  libx11-dev libxau-dev libxcursor-dev libxdmcp-dev libxext-dev libxft-dev
  libxi-dev libxinerama-dev libxmu-dev libxmu-headers libxrandr-dev
  libxrender-dev libxt-dev mesa-common-dev pkg-config qt4-designer
  qt4-dev-tools qt4-doc qt4-qtconfig x-dev x11proto-core-dev
  x11proto-fixes-dev x11proto-input-dev x11proto-kb-dev x11proto-randr-dev
  x11proto-render-dev x11proto-xext-dev x11proto-xinerama-dev zlib1g-dev
0 packages upgraded, 47 newly installed, 0 to remove and 0 not upgraded.
Need to get 31.1MB of archives. After unpacking 109MB will be used.
The following packages have unmet dependencies:
  libglu1-mesa-dev: Depends: libglu1-mesa (= 6.4.1-0ubuntu8) but 6.5.1-cvs20060628 is installed.
  libgl1-mesa-dev: Depends: libgl1-mesa (= 6.4.1-0ubuntu8) but 6.5.1-cvs20060628 is installed.
  libxfixes-dev: Depends: libxfixes3 (= 1:3.0.1.2-0ubuntu3) but 1:4.0-0ubuntu1 is installed.
Resolving dependencies...
The following actions will resolve these dependencies:

Keep the following packages at their current version:
libgl1-mesa-dev [Not Installed]
libglu1-mesa-dev [Not Installed]
libqt4-dev [Not Installed]
libxcursor-dev [Not Installed]
libxfixes-dev [Not Installed]
qt4-designer [Not Installed]
qt4-dev-tools [Not Installed]

Score is 55

Accept this solution? [Y/n/q/?] Y
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Do you want to continue? [Y/n/?] Y
Writing extended state information... Done

```

And when I attempt the compile, just in case it helps:
```

unichr:$ qmake
unichr:$ make
g++ -c -pipe -Wall -W -O2 -D_REENTRANT  -DQT_NO_DEBUG -DQT_THREAD_SUPPORT -I/usr/share/qt3/mkspecs/default -I. -I/usr/share/qt3/include -o main.o main.cpp
main.cpp:13:24: error: QApplication: No such file or directory
In file included from main.cpp:15:
unichart.h:16:23: error: QMainWindow: No such file or directory
unichart.h:31: error: expected class-name before &#8216;{&#8217; token
unichart.h:32: error: ISO C++ forbids declaration of &#8216;Q_OBJECT&#8217; with no type
unichart.h:34: error: expected &#8216;;&#8217; before &#8216;private&#8217;
unichart.h:52: error: expected `)' before &#8216;*&#8217; token
unichart.h:55: error: expected `:' before &#8216;slots&#8217;
unichart.h:56: error: expected primary-expression before &#8216;void&#8217;
unichart.h:56: error: ISO C++ forbids declaration of &#8216;slots&#8217; with no type
unichart.h:56: error: expected &#8216;;&#8217; before &#8216;void&#8217;
unichart.h:58: error: expected &#8216;,&#8217; or &#8216;...&#8217; before &#8216;&&#8217; token
unichart.h:58: error: ISO C++ forbids declaration of &#8216;QString&#8217; with no type
main.cpp: In function &#8216;int main(int, char**)&#8217;:
main.cpp:19: error: &#8216;QApplication&#8217; was not declared in this scope
main.cpp:19: error: expected `;' before &#8216;app&#8217;
main.cpp:22: error: &#8216;class UniChart&#8217; has no member named &#8216;show&#8217;
main.cpp:24: error: &#8216;app&#8217; was not declared in this scope
main.cpp: At global scope:
main.cpp:17: warning: unused parameter &#8216;argc&#8217;
main.cpp:17: warning: unused parameter &#8216;argv&#8217;
make: *** [main.o] Error 1

```

---

### Post by po0f on 2006-12-18
Bigglez,

If you notice the first compile command, it is including (-I as in eye) Qt3 headers (-I/usr/share/qt3/include).

I just noticed the version of Mesa headers installed; you don't happen to be using Beryl or the like, are you?  Maybe you could try commenting out your Beryl repos in /etc/apt/sources.list, updating apt, installing libqt4-dev, uncommenting your Beryl repos, and reinstalling the needed packages for Beryl again.  (I really wouldn't recommend this, but it might be a possible solution.)

---

### Post by Bigglez on 2006-12-18
Po0f,
I see the refs to qt3 now (I'm not all that clued-up on C and make and so on), but the INSTALL file for this app specifies QT4, so it's defn an error on the part of the programmer.

Perhaps I have just chosen a dud source-file as my first attempt at compiling a QT app on Kubuntu! (I have done it often on Fedora, but that comes with dev-stuff already working)

As to Beryl, no not since a tiny flirt with xgl/compiz a few months ago and it has been commented-out in my sources for ages (I posted my sources.list on page 1)

Do you think I should remove these:
```

The following packages have unmet dependencies:
  libglu1-mesa-dev: Depends: libglu1-mesa (= 6.4.1-0ubuntu8) but 6.5.1-cvs20060628 is installed.
  libgl1-mesa-dev: Depends: libgl1-mesa (= 6.4.1-0ubuntu8) but 6.5.1-cvs20060628 is installed.
  libxfixes-dev: Depends: libxfixes3 (= 1:3.0.1.2-0ubuntu3) but 1:4.0-0ubuntu1 is installed.

```
? But is Aptitude cannot change 'em, should I...?

How would I remove xgl/compiz properly -- not a fair question, I realize I'm opening a can of worms here. Perhaps I should search for threads to that effect.

Thanks for the help so far!
:)

---

### Post by po0f on 2006-12-18
Bigglez,

I would try manually reinstalling those packages, and if that doesn't work, uninstalling and reinstalling the packages.

As for uninstalling Xgl/Compiz, try looking for the how-to you followed and removing the packages it tells you to install.  (Another reason to use aptitude, it will remove all the packages automatically brought in when you remove a package you installed.)  :)

---

### Post by Bigglez on 2006-12-18
Thanks for trying to help po0f. It looks like I am severely scr*wed on those three files. I can't remove them because a whole pyramid of other stuff rests on them and they are actually *newer* versions of the files that the libqt4-dev packages wants me to have...

So the question is how to *down-version* those files?

Why do I have this urge to type your nick as 'fo0b'? :D

---

### Post by Bigglez on 2006-12-18
For completeness, I include here the solution to the problem I had. Thanks to po0f for getting me most of the way there:

**Summary:**
1. I wanted to install "QT-dev" stuff. Asked forum about it.
2. Eventually found I needed "libqt3-mt-dev" package.
3. I found I could not install it because there was a problem with other packages clashing with it. Specifically:
```

The following packages have unmet dependencies:
  libglu1-mesa-dev: Depends: libglu1-mesa (= 6.4.1-0ubuntu8) but 6.5.1-cvs20060628 is installed.
  libgl1-mesa-dev: Depends: libgl1-mesa (= 6.4.1-0ubuntu8) but 6.5.1-cvs20060628 is installed.
Resolving dependencies...

```
4. The problem was because I had installed stuff from dodgy repos (Glx/compiz). If you look at the version numbers above, you will see that the version of 'libgl1-mesa' I had installed was 6.**5**.1.blahblah and the version that Aptitude (apt-get) wanted was 6.**4**.1.blahblah... The file I want to install (libqt3-mt-dev) wants LOWER versions of other stuff on my system! Gasp !
**The question was "How to downgrade a package?"**
5. Hit Ubuntu Forums. Search, and search and search. No results.
6. Hit google. One search, bang! a clue. (On the forum :) )
This is what I did:
1. Typed:
apt-cache showpkg libgl1-mesa
2. Looked at the end of the output:```

Provides:
6.5.1-cvs20060628 - libglu1
6.4.1-0ubuntu8 - libglu1

```
3. Copy the LOWER version number: 6.4.1-0ubuntu8
4. Type this: 
sudo aptitude install libgl1-mesa**=6.4.1-0ubuntu8**

That install the package with a specific version number, replacing the one you had already. So you have now DOWNGRADED the package. The trick is the equal sign.

I then did the same for the libglu1-mesa package and after that I was able to install my libqt3-mt-dev

HTH - and hope I didn't do anything dumb.

All sorted. (Until the next reboot ... :| )

:D

---

### Post by po0f on 2006-12-18
Bigglez,

I'm glad you got it all sorted out.  I was going to point out the installing specific versions with apt-get/aptitude (using package name followed by equal sign and version) but I had to run off to work this morning.

---

### Post by der_joachim on 2006-12-19
> **Bigglez said:**
> Hi, don't know that one. What is <yourpackage> supposed to be?

Simple. The name of the package you want to install. Note that the package should be in one of your repositories! For instance, if you want to compile wine, use the follwoing three commands: 

```

sudo apt-get build-dep wine
sudo apt-get --build source wine
sudo dpkg -i *.deb

```
The first command will satisfy any dependencies (there is no aptitude equivalent for this IIRC). The second one will do the actual compilation and builds the packages. The third command installs them.

---

