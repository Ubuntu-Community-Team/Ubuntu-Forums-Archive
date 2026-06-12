---
title: "Building knights, problem with qt :("
date: 2005-07-14
forum: General Help
---

### Post by pirrax on 2005-07-14
Hi all.

I tried to build the chess front end knights ([http://knights.sourceforge.net/)](http://knights.sourceforge.net/)), and I have problem with qt.  libqt3-mt-dev and libqt3c102-mt are installed (as adviced in [http://www.ubuntuforums.org/showpost.php?p=188806&postcount=11)](http://www.ubuntuforums.org/showpost.php?p=188806&postcount=11)).  Starting configure gave me this error msg:

> checking for Qt... configure: error: Qt (>= Qt 3.0) (headers and libraries) not found. Please check your installation!
For more details about this problem, look at the end of config.log.

From knights mailinglist I found this out:
[http://sourceforge.net/mailarchive/forum.php?thread_id=2845433&forum_id=1142](http://sourceforge.net/mailarchive/forum.php?thread_id=2845433&forum_id=1142)
> From: Troy Corbin Jr. <tcorbin@us...>
Re: need help on installing knights on Debian  
2003-07-28 18:59

 On Sunday 27 July 2003 04:22 pm, felix_do wrote:
 > Hello,
 > I was trying to compile knights on my Debian 3.0 box, but at "configure"
 > i got the message that i don"t have
 > Qt installed. Having installed the debian packages "libqt3" "libqt3-dev"
 > "libqt3-headers" the error still comes up.
 > Anyone knows which packages are wrong/missing?
 
 Though I don"t run Debian, it sounds like you have the correct packages. 
 Perhaps you"ll need to tell "configure" where your Qt is installed. For 
 example:
 
 configure --with-qt-dir=/usr/qt
 
 or
 
 configure --with-qt-includes=/usr/include --with-qt-libraries=/usr/lib
 
 You"ll find several more options by running "configure --help".
 
 I hope this helps. :-)
 -- 
 Troy Corbin Jr.
 troy@kn...
 [http://www.knights-chess.com](http://www.knights-chess.com)

If I try to install with 
> ./configure --with-qt-dir=/usr/share/qt3
or 
> ./configure --with-qt-includes=/usr/share/qt3/include --with-qt-libraries=/usr/lib

the result is:

> checking for Qt... configure: error: Qt (>= Qt 3.0) (library qt-mt) not found. Please check your installation!
For more details about this problem, look at the end of config.log.
Make sure that you have compiled Qt with thread support!

under /usr/lib is a linked file named libqt-mt.so.  I thought, that is the file configure looking for, or am I wrong?

I tried to install libqt3-compat-headers, all libqt3c102-mt*, but I still had no luck.

Do you have any idea, which package I do have to install?  Thanks for any help.

---

### Post by Xian on 2005-07-14
Try installing the kdelibs4-dev and xlibs-dev packages.

---

### Post by pirrax on 2005-07-14
hi,
kdelibs4-dev package is already installed.
I installed xlibs-dev, but after that I still do get the same error msg from configure :(

---

### Post by rlklee on 2005-07-20
I'm having the same problem.  All the relevant packages seemed to be installed.

---

### Post by rlklee on 2005-07-20
Fixed it.  configure with this arg: --with-qt-lib=/usr/share

(That's where mine is anyways.)

---

### Post by pirrax on 2005-07-26
[QUOTE=][/QUOTE]
 I still can't configure it.  Can you post the list of your packages?

I don't know how, but perhaps someone from ubuntu can tell how?

Did you compile and install qt by yourself?  Because I am using the qt package from ubuntu and it is in /usr/share/qt3

---

### Post by rubengs on 2005-08-07
Howto install Knights from last released rpm: 

1. Download the rpm from sourceforge: 
[http://puzzle.dl.sourceforge.net/sourceforge/knights/knights-0.6-0.i386.rpm](http://puzzle.dl.sourceforge.net/sourceforge/knights/knights-0.6-0.i386.rpm)
(you can browse that directory to find the latest version)

2. $ sudo alien knights-0.6-0.i386.rpm

3. $ sudo dpkg -i knights-0.6-0.i386.deb 

This worked for me, no need to compile.

---

