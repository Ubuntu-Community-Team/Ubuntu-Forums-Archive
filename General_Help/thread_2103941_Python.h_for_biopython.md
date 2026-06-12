---
title: "Python.h for biopython?"
date: 2013-01-11
forum: General Help
---

### Post by naragam on 2013-01-11
Hi,

Am trying to get a brand new pc to become a developer's platform for bioinformatics research and need to put in all the foundation libs and packages... I thought there was  some ubuntu package that gives one all the developers tools and more. Can anyone point me to it please?

Thanks much in advance,

Nash

---

### Post by steeldriver on 2013-01-11
it kind of sounds like you're talking about the build-essential package - although afaik that only provides the C/C++ packages (gcc, g++, make, etc.) plus some stuff specifically for building Debian packages themselves

I'm not aware of anything specifically for python, not even sure what python.h would be required for??

---

### Post by naragam on 2013-01-11
Well,  Python.h is needed for building biopython package and I got a bunch of debian stuff for getting the so-called "deleted" python3-dev package in ubuntu 12.04 LTS....

But so far, my attempts have been unsuccessful.... I still haven't been able to get the pesky Python.h file....

Anybody help me ??

TiA, Nash

---

### Post by steeldriver on 2013-01-11
```
$ apt-file search -x '\/Python.h$'
pypy-dev: /usr/lib/pypy/include/Python.h
python2.7-dbg: /usr/include/python2.7_d/Python.h
python2.7-dev: /usr/include/python2.7/Python.h
python3.2-dbg: /usr/include/python3.2dmu/Python.h
python3.2-dev: /usr/include/python3.2mu/Python.h
```

---

### Post by naragam on 2013-01-11
Okay thanks much.... I see that my installation does have a couple of Python.h files in the following dirs -

pypy-dev: /usr/lib/pypy/include/Python.h
python2.7-dbg: /usr/include/python2.7_d/Python.h
python2.7-dev: /usr/include/python2.7/Python.h
python3.2-dbg: /usr/include/python3.2dmu/Python.h
python3.2-dev: /usr/include/python3.2mu/Python.h

...just like yours; however, I fail building biopython for lacking that include file. Any ideas about how to use these include paths into the build script setup.py?

TiA, Nash

---

### Post by steeldriver on 2013-01-11
it depends what the script looks like, you might want to use pkg-config in your Makfile's CFLAGS / CXXLAGS / CPPFLAGS

```
$ pkg-config --cflags python
-I/usr/include/python2.7
```

You will probably need to do something similar for the libs

---

### Post by naragam on 2013-01-11
Well....I don't see any Makefile other than in the Doc subdir (confusing as hell...lol) abd forget the usual -I flag we use in Makefiles. This build uses a python script to build the libs and store whatever else and I have never seen setting up Makefile in a ../Doc directory!

I suppose I could try adding the paths there, but it irks me not to understand the build script and the dependency set up there in...

Nash

---

