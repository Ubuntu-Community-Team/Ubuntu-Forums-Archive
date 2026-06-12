---
title: "Comix - pygtk not found?"
date: 2007-07-29
forum: General Help
---

### Post by andb on 2007-07-29
Some help with the python program Comix would be greatly appreciated.

After installing Comix from both the repositories and from source, i get the following error when trying to run:
```
$comix
PyGTK version 2.8.0 or higher is required to run Comix.
No version of PyGTK was found on your system.
```
```
$ sudo aptitude search python |grep gtk
p   galago-gtk-python               - Python bindings for libgalago-gtk         
v   python-dbgtk                    -                                           
i   python-gtk-1.2                  - GTK support module for Python             
i   python-gtk2                     - Python bindings for the GTK+ widget set   
i   python-gtk2-dev                 - GTK+ bindings: devel files                
p   python-gtk2-doc                 - Python bindings for the GTK+ widget set - 
p   python-gtk2-tutorial            - tutorial for the GTK2 python library      
i   python-gtkhtml2                 - Python bindings for the GtkHTML2 library  
p   python-gtkmvc                   - model-view-controller (MVC) implementation
i   python-wxgtk2.4                 - wxWindows Cross-platform C++ GUI toolkit (
i   python-wxgtk2.6                 - wxWidgets Cross-platform C++ GUI toolkit (
i A python-wxgtk2.8                 - wxWidgets Cross-platform C++ GUI toolkit (
v   python2.4-gtk2                  -                                           
v   python2.4-wxgtk2.6              -                                           
v   python2.5-gtk2                  -   
```

I also installed, using dpkg, python-gtk2 2.10.3-0ubuntu3 from [https://launchpad.net/ubuntu/edgy/i386/python-gtk2](https://launchpad.net/ubuntu/edgy/i386/python-gtk2)

So, it seems to me that i do have pygtk, and it is at least ver 2.8. Also surprising is that the dependencies would be unmet despite installing from repositories.  Can someone tell me what's going wrong here? Thanks!

---

### Post by dando80 on 2007-07-30
Have you actually installed the packages?? apt-cache search will show you available packages but it doesn't mean they are installed. Use apt-get install pkgname , aptitude install pkgname or synaptic to actually install them.

---

### Post by andb on 2007-07-31
Unless something is really broken, the "i" on the left of the output from apt-get search indicates that the package is installed. Yes, I installed first via aptituted and then downloaded the actual .deb package from launchpad.net and installed using dpkg. 

I just installed Wah!cade (a xmame front end) which also reports that there is no pyGTK. I do, however, use Quod Libet to play music, which I believe also uses pyGTK, and it works fine.  Hmmm. Hope the easiest answer isn't a reinstall, Ive got a ton of hand configured software (none using python though).

---

### Post by dando80 on 2007-07-31
Which version of ubuntu are you using? Can you show us "aptitude show python-gtk2 | head"

Thanks.

---

