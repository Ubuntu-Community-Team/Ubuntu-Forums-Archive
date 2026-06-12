---
title: "&quot;make&quot; - no target specified - during GTK+ install"
date: 2006-12-20
forum: General Help
---

### Post by Get_Ya_Wicked_On on 2006-12-20
I just downloaded the latest GTK+ to start doing some GUI programming with my C skills and:

After untarring, moving to the directory, "./configure", and then "make" it gives me this...

```

elephant@elephant:~/gtk+-2.10.6$ make

make: *** No targets specified and no makefile found.  Stop.

```

I'm relatively new to doing this. Thanks in advance for your efforts.

**EDIT:** Well, I have it down to one dependency keeping it from being built. Tiff. Can ANYONE help wit this? It does not want to be ./configure'd

---

### Post by bodhi.zazen on 2006-12-20
> **Get_Ya_Wicked_On said:**
> I'm relatively new to doing this. Thanks in advance for your efforts.

**EDIT:** Well, I have it down to one dependency keeping it from being built. Tiff. Can ANYONE help wit this? It does not want to be ./configure'd

[list=number][*]Did ./configure give error message ?
[*]If so, what ?
[*]If not post output of ls -a[/list]

---

### Post by Get_Ya_Wicked_On on 2006-12-20
Thank you so much for your reply. I just got it working.

I just installed the Tifflib through synaptic and GTK finally built itself.

And I can not wait to start making Linux programs w/ a GUI. This is awesome.

---

### Post by po0f on 2006-12-20
Get_Ya_Wicked_On,

Installing two different versions of the same library will probably break your system if you don't know what you are doing.  Why are you custom compiling GTK 2.10.6?  Are you on Edgy?  If so, this is the default, just install libgtk2.0-dev and you should be all set to develop GTK2.0 apps.

---

### Post by lenluin on 2007-02-27
I have the same problem... I'll post my ls -a....



.             config.log    gdl.kdevelop  Makefile.am    README
..            config.sub    gdl.kdevses   Makefile.cvs   src
aclocal.m4    configure     HACKING       Makefile.in    templates
AUTHORS       configure.in  INSTALL       missing        testsuite
ChangeLog     COPYING       install-sh    mkinstalldirs  TODO
config.guess  depcomp       libtool       NEWS
config.h.in   Doxyfile      ltmain.sh     PYTHON.txt

---

