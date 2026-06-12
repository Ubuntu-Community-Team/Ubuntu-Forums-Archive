---
title: "Redhat Cluster Suite"
date: 2007-02-01
forum: General Help
---

### Post by sasha12 on 2007-02-01
I am using Ubunut6.06 AMD64 .

Having trouble using the redhat-cluster-suite package ... 

I also installed the Graphical configuration package system-config-cluster  but I get a runtime error when I run system-config-cluster :

Traceback (most recent call last):
  File "/usr/sbin/system-config-cluster", line 17, in ?
    import MessageLibrary
  File "/usr/share/system-config-cluster/MessageLibrary.py", line 1, in ?
    import gtk
  File "/usr/lib/python2.4/site-packages/gtk-2.0/gtk/__init__.py", line 45, in ?
    from _gtk import *
RuntimeError: could not open display

So it is not starting ... I tried starting it from xubuntu desktop and nothing happens and I 
don't see anything in logs .

Anyone seen this before .

---

### Post by sasha12 on 2007-02-06
Solved :

Need to login to xubuntu as root ... in order to do this you have to enable root login ...

In GNOME , Applications -> System -> Login Window ... here you will find settings for
changing this ... I also unchecked 'Deny TCP Connections to XServer' ; did not check yet if
this has effect as well .

---

