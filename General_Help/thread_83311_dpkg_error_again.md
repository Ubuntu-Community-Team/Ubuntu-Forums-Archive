---
title: "dpkg error again"
date: 2005-10-28
forum: General Help
---

### Post by Daniloc on 2005-10-28
root@daniloc:/home/daniloc # apt-get upgrade
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
root@daniloc:/home/daniloc #


:(
 How to fix this...

When i type 
dpkg --configure -a

root@daniloc:/home/daniloc # dpkg --configure -a
Setting up libcdk4 (4.9.9-3.2) ...

Setting up libsigc++0c102 (1.0.4-6.1) ...

Setting up libsigc++-dev (1.0.4-6.1) ...
Setting up ickle-common (0.3.2-3) ...
dpkg: dependency problems prevent configuration of licq-plugin-jonsgtk:
 licq-plugin-jonsgtk depends on licq (>= 1.3.0); however:
  Package licq is not installed.
 licq-plugin-jonsgtk depends on licq (<< 1.3.1); however:
  Package licq is not installed.
dpkg: error processing licq-plugin-jonsgtk (--configure):
 dependency problems - leaving unconfigured
Setting up libgtkmm1.2-0 (1.2.10-7) ...

dpkg: dependency problems prevent configuration of licq-plugin-qt:
 licq-plugin-qt depends on licq (= 1.3.0-2ubuntu1); however:
  Package licq is not installed.
dpkg: error processing licq-plugin-qt (--configure):
 dependency problems - leaving unconfigured
Setting up libmodplug0 (0.7-3) ...

Setting up libicq2000-doc (0.3.2-3) ...
Setting up libgpgme6 (0.3.16-2) ...

dpkg: dependency problems prevent configuration of licq-plugin-osd:
 licq-plugin-osd depends on licq (= 1.3.0-2ubuntu1); however:
  Package licq is not installed.
dpkg: error processing licq-plugin-osd (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of licq-plugin-kde:
 licq-plugin-kde depends on licq (= 1.3.0-2ubuntu1); however:
  Package licq is not installed.
dpkg: error processing licq-plugin-kde (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of licq-plugin-rms:
 licq-plugin-rms depends on licq (= 1.3.0-2ubuntu1); however:
  Package licq is not installed.
dpkg: error processing licq-plugin-rms (--configure):
 dependency problems - leaving unconfigured
Setting up libicq2000 (0.3.2-3) ...

Setting up libicq2000-dev (0.3.2-3) ...
Setting up ickle (0.3.2-3) ...

Setting up ickle-control (0.3.2-3) ...
Errors were encountered while processing:
 licq-plugin-jonsgtk
 licq-plugin-qt
 licq-plugin-osd
 licq-plugin-kde
 licq-plugin-rms
root@daniloc:/home/daniloc #


And what i need to do?

---

### Post by tehwa on 2005-10-28
Perhaps open Synaptic and find these packages using the 'Broken' filter from the sidebar (Custom Button). Uncheck these packages and whatever depends on them.

---

### Post by inlivingcolour on 2005-10-29
Im having the same problem with dpkg, except its hanging up while trying to connect to a website to download something.  And, I cant do anything like install programs via terminal or Synaptic until i do the dpkg --configure -a thing.  Synaptic comes up with nothing when I search for broken packages.  How do I fix this?

---

