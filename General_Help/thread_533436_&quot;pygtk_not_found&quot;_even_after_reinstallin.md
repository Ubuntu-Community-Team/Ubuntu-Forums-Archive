---
title: "&quot;pygtk not found&quot; even after reinstalling python-gtk2"
date: 2007-08-23
forum: General Help
---

### Post by mooglinux on 2007-08-23
alrihgt, this is a problem that has been plagueing me for a week or two now. I installed compiz-fusion from the instructions here: [http://kevin.vanzonneveld.net/techblog/article/enable_compizfusion_in_ubuntu_feisty/]("http://kevin.vanzonneveld.net/techblog/article/enable_compizfusion_in_ubuntu_feisty/")
and at first, it did not work. after several retrys, i have compiz-fusion running great, aside from one minor problem: i cannot get into my settings manager! after messing around i have determined the problem not to be the settings manager but python. gmail-notify and ccsm both return "no package named pygtk" 

i have reinstalled, uninstalled and installed, compiled from source, and nothing works. apt-get remove python-gtk2 removed half my desktop with it, and i had to install ubuntu-desktop from terminal. i watched closely to see it uninstall python-gtk2 and later install it. gmail-notify and ccsm still tell me that there is no module names pygtk, even tho i can find python-gtk2 in synaptic and have installed it again and again. i have reinstalled many python packages through synaptic, and nothing has helped. 

it appears as though its installed however nothing can see it.  after searching through other threads with a similar problem, i have found several commands people have requested for info about python and hte like that i will add here, but i cannot get any solutions to work. mentioned has been paths? i have no idea what they are or how to fix them but it is the only thing i have seen that i havent tried to some degree. i am new to ubuntu, so specific commands would be much appreciated.

> mooglinux@gaurdian:~$ sudo aptitude show python-gtk2 | head
Package: python-gtk2
State: installed
Automatically installed: no
Version: 2.10.4-0ubuntu3
Priority: optional
Section: python
Maintainer: Ubuntu Core developers <ubuntu-devel-discuss@lists.ubuntu.com>
Uncompressed Size: 6570k
Depends: python-support (>= 0.3.4), python (< 2.6), python (>= 2.4), libatk1.0-0
         (>= 1.13.1), libc6 (>= 2.5-0ubuntu1), libcairo2 (>= 1.3.14),



> mooglinux@gaurdian:~$ sudo aptitude search python |grep gtk
p   galago-gtk-python               - Python bindings for libgalago-gtk         
v   python-dbgtk                    -                                           
i   python-gtk-1.2                  - GTK support module for Python             
i   python-gtk2                     - Python bindings for the GTK+ widget set   
p   python-gtk2-dbg                 - Python bindings for the GTK+ widget set (d
p   python-gtk2-dev                 - GTK+ bindings: devel files                
p   python-gtk2-doc                 - Python bindings for the GTK+ widget set - 
p   python-gtk2-tutorial            - tutorial for the GTK2 python library      
i   python-gtkhtml2                 - Python bindings for the GtkHTML2 library  
p   python-gtkhtml2-dbg             - Python bindings for the GtkHTML2 library (
p   python-gtkmvc                   - model-view-controller (MVC) implementation
p   python-wxgtk2.4                 - wxWindows Cross-platform C++ GUI toolkit (
i   python-wxgtk2.6                 - wxWidgets Cross-platform C++ GUI toolkit (
p   python-wxgtk2.6-dbg             - wxWidgets Cross-platform C++ GUI toolkit (
p   python-wxgtk2.8                 - wxWidgets Cross-platform C++ GUI toolkit (
p   python-wxgtk2.8-dbg             - wxWidgets Cross-platform C++ GUI toolkit (
v   python2.4-gtk2                  -                                           
v   python2.5-gtk2                  -                                           
v   python2.5-wxgtk2.6              -                                           
v   python2.5-wxgtk2.8              -  

---

### Post by mooglinux on 2007-08-25
might also want to add that im using the x86_64 version of ubuntu

---

### Post by apetresc on 2007-08-25
Have you tried installing the python-gtk2-dev package as well?```
sudo apt-get install python-gtk2-dev
``` And then ```
adrian@rootbeer:~/Desktop/subs$ python
Python 2.5.1 (r251:54863, May  2 2007, 16:56:35)
[GCC 4.1.2 (Ubuntu 4.1.2-0ubuntu4)] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> import pygtk
>>>
```

Let me know if that helps.

---

### Post by mooglinux on 2007-08-25
> mooglinux@gaurdian:~$ python
Python 2.5.1 (r251:54863, Aug 13 2007, 21:04:37) 
[GCC 4.1.2 (Ubuntu 4.1.2-0ubuntu4)] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> import pygtk
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
ImportError: No module named pygtk
>>> 


no luck, altho i did not have that package installed. perhaps i will need to look for any other packages that were not reinstalled. 

another note, is it a problem running multiple versions of python? i understand that it is not backwerds compatible, and i dont know if blender uses python 2.5 i believe it might use 2.4, for example. on windows i did not have trouble running several different versions

---

