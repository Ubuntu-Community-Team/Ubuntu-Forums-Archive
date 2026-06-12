---
title: "Python Pillow Library Install Problem"
date: 2013-04-02
forum: General Help
---

### Post by rwethereyet on 2013-04-02
ubuntu 12.10, python3.3 32 bit version

I have a python 3.3 test program which runs on Win 7 and uses the new  Pillow-2.0.0 (new fork of PIL) which was installed using the windows  installer provided.  So, I know my little python program should work.

However on LINUX, I can not get the library to install properly.  I  should mention that I use both python 2.7 (my default) and also python  3.3, so when I run the PIL setup.py program I invoke 'python3.3 setup.py  install' .  

The Pillow library requires external jpeg support and the installation  instructions specify doing sudo apt-get install libjpeg62-dev 'before'  building and installing the python Pillow library.  When built it does  properly indicate '--- JPEG support available' .  

However, when I run my 'python3.3 test.py' program I get an exception  'builtins.OSError: decoder jpeg not available'.  So, it is not finding  the JPEG library during the build or install (although it seems to  indicate that it did by saying JPEG support available).  

Any suggestions how I can learn what is wrong ?  I must have something  misconfigured and it might have something to do with my running python  2.7 as my default, but I am not sure.

There is a link to libjpeg.so in /usr/lib to the newly installed  /usr/lib/i386-linux-gnu.  There are some other references to libjpeg.so .   

What path setup.py build looks for to find the libraries ?

---

