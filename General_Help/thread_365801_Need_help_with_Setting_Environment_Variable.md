---
title: "Need help with Setting Environment Variable"
date: 2007-02-20
forum: General Help
---

### Post by ramjet_1953 on 2007-02-20
Hi, Guys!

I am fairly new with using the command line and am almost there in compiling and installing the program pdfEdit.

The [COLOR="Red"]./compile[/COLOR] and the [COLOR="Red"]make[/COLOR] commands all went well, but when I do a [COLOR="Red"]sudo make install[/COLOR] I get the following error.

[COLOR="Blue"]roger@roger-laptop:~$ cd /home/roger/downloads/pdfedit/version-0.2.5/pdfedit-0.2.5
roger@roger-laptop:~/downloads/pdfedit/version-0.2.5/pdfedit-0.2.5$ sudo make install
cd doc && ( gmake doc_dist|| make doc_dist )
/bin/sh: gmake: not found
make[1]: Entering directory `/home/roger/downloads/pdfedit/version-0.2.5/pdfedit-0.2.5/doc'
cd user && ( gmake all_no_pdf || make all_no_pdf )
/bin/sh: gmake: not found
make[2]: Entering directory `/home/roger/downloads/pdfedit/version-0.2.5/pdfedit-0.2.5/doc/user'
make[2]: Nothing to be done for `all_no_pdf'.
make[2]: Leaving directory `/home/roger/downloads/pdfedit/version-0.2.5/pdfedit-0.2.5/doc/user'
cd design && ( gmake all_no_pdf || make all_no_pdf )
/bin/sh: gmake: not found
make[2]: Entering directory `/home/roger/downloads/pdfedit/version-0.2.5/pdfedit-0.2.5/doc/design'
make[2]: Nothing to be done for `all_no_pdf'.
make[2]: Leaving directory `/home/roger/downloads/pdfedit/version-0.2.5/pdfedit-0.2.5/doc/design'
make[1]: Leaving directory `/home/roger/downloads/pdfedit/version-0.2.5/pdfedit-0.2.5/doc'
cd src && make
make[1]: Entering directory `/home/roger/downloads/pdfedit/version-0.2.5/pdfedit-0.2.5/src'
cd xpdf && make libxpdf
make[2]: Entering directory `/home/roger/downloads/pdfedit/version-0.2.5/pdfedit-0.2.5/src/xpdf'
cd goo; make
make[3]: Entering directory `/home/roger/downloads/pdfedit/version-0.2.5/pdfedit-0.2.5/src/xpdf/goo'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/roger/downloads/pdfedit/version-0.2.5/pdfedit-0.2.5/src/xpdf/goo'
cd fofi; make
make[3]: Entering directory `/home/roger/downloads/pdfedit/version-0.2.5/pdfedit-0.2.5/src/xpdf/fofi'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/roger/downloads/pdfedit/version-0.2.5/pdfedit-0.2.5/src/xpdf/fofi'
cd splash; make
make[3]: Entering directory `/home/roger/downloads/pdfedit/version-0.2.5/pdfedit-0.2.5/src/xpdf/splash'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/roger/downloads/pdfedit/version-0.2.5/pdfedit-0.2.5/src/xpdf/splash'
cd xpdf; make libxpdf
make[3]: Entering directory `/home/roger/downloads/pdfedit/version-0.2.5/pdfedit-0.2.5/src/xpdf/xpdf'
make[3]: Nothing to be done for `libxpdf'.
make[3]: Leaving directory `/home/roger/downloads/pdfedit/version-0.2.5/pdfedit-0.2.5/src/xpdf/xpdf'
make[2]: Leaving directory `/home/roger/downloads/pdfedit/version-0.2.5/pdfedit-0.2.5/src/xpdf'
cd utils && make
make[2]: Entering directory `/home/roger/downloads/pdfedit/version-0.2.5/pdfedit-0.2.5/src/utils'
make[2]: `libutils.a' is up to date.
make[2]: Leaving directory `/home/roger/downloads/pdfedit/version-0.2.5/pdfedit-0.2.5/src/utils'
cd kernel && /bin/qmake && make staticlib
make[2]: Entering directory `/home/roger/downloads/pdfedit/version-0.2.5/pdfedit-0.2.5/src/kernel'
make[2]: Nothing to be done for `staticlib'.
make[2]: Leaving directory `/home/roger/downloads/pdfedit/version-0.2.5/pdfedit-0.2.5/src/kernel'
cd kpdf-kde-3.3.2 && /bin/qmake && make staticlib
make[2]: Entering directory `/home/roger/downloads/pdfedit/version-0.2.5/pdfedit-0.2.5/src/kpdf-kde-3.3.2'
make[2]: Nothing to be done for `staticlib'.
make[2]: Leaving directory `/home/roger/downloads/pdfedit/version-0.2.5/pdfedit-0.2.5/src/kpdf-kde-3.3.2'
cd qsa && ./configure
[COLOR="Red"]Can't find Qt library. No QTDIR set.
make[1]: *** [qsa/Makefile.qsa] Error 1
make[1]: Leaving directory `/home/roger/downloads/pdfedit/version-0.2.5/pdfedit-0.2.5/src'
make: *** [src] Error 2[/COLOR]
roger@roger-laptop:~/downloads/pdfedit/version-0.2.5/pdfedit-0.2.5$ [/COLOR]

As you can see it involves setting up the environment variable for QTDIR.
I have no idea how to do this. Can someone help?

Regards,
Roger :cool:

---

### Post by phossal on 2007-02-20
I'm not totally sure, but that looks like a *dependency* error, rather than an environment variable error. There is a package you want to download. You might want *libqt4-core*

---

### Post by ramjet_1953 on 2007-02-20
I'm sorry, I should have made it clearer in my previous posting, I have all of the necessary libraries, to fulful the depandency requirements.

I just need to know how to set the environment variable for qtdir.

Regards,
Roger :cool:

---

### Post by phossal on 2007-02-20
Environment variables are easy, but you may be looking for this:
[http://www.digitalfanatics.org/projects/qt_tutorial/chapter04.html](http://www.digitalfanatics.org/projects/qt_tutorial/chapter04.html)

---

### Post by ramjet_1953 on 2007-02-20
Thaks for that!

That was all I needed to do.

You are a STAR **************************

Regards,
Roger :cool:

---

### Post by phossal on 2007-02-20
Hey, you're welcome! ;) Thanks for letting me know you figured it out.

---

