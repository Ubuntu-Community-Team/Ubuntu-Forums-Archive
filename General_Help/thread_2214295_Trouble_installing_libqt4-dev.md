---
title: "Trouble installing libqt4-dev"
date: 2014-03-31
forum: General Help
---

### Post by tivatranquio on 2014-03-31
I just want to install this package but that is the result:

 sudo apt-get install libqt4-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 libqt4-dev : Depends: libqt4-dbus (= 4:4.8.1-0ubuntu4.6) but 4:4.8.1-0ubuntu5~precise1~test1 is to be installed
              Depends: libqt4-declarative (= 4:4.8.1-0ubuntu4.6) but 4:4.8.1-0ubuntu5~precise1~test1 is to be installed
              Depends: libqt4-designer (= 4:4.8.1-0ubuntu4.6) but it is not going to be installed
              Depends: libqt4-help (= 4:4.8.1-0ubuntu4.6) but it is not going to be installed
              Depends: libqt4-network (= 4:4.8.1-0ubuntu4.6) but 4:4.8.1-0ubuntu5~precise1~test1 is to be installed
              Depends: libqt4-qt3support (= 4:4.8.1-0ubuntu4.6) but it is not going to be installed
              Depends: libqt4-script (= 4:4.8.1-0ubuntu4.6) but 4:4.8.1-0ubuntu5~precise1~test1 is to be installed
              Depends: libqt4-scripttools (= 4:4.8.1-0ubuntu4.6) but it is not going to be installed
              Depends: libqt4-sql (= 4:4.8.1-0ubuntu4.6) but 4:4.8.1-0ubuntu5~precise1~test1 is to be installed
              Depends: libqt4-svg (= 4:4.8.1-0ubuntu4.6) but 4:4.8.1-0ubuntu5~precise1~test1 is to be installed
              Depends: libqt4-test (= 4:4.8.1-0ubuntu4.6) but it is not going to be installed
              Depends: libqt4-xml (= 4:4.8.1-0ubuntu4.6) but 4:4.8.1-0ubuntu5~precise1~test1 is to be installed
              Depends: libqt4-xmlpatterns (= 4:4.8.1-0ubuntu4.6) but 4:4.8.1-0ubuntu5~precise1~test1 is to be installed
              Depends: libqtcore4 (= 4:4.8.1-0ubuntu4.6) but 4:4.8.1-0ubuntu5~precise1~test1 is to be installed
              Depends: libqtgui4 (= 4:4.8.1-0ubuntu4.6) but 4:4.8.1-0ubuntu5~precise1~test1 is to be installed
              Depends: qt4-linguist-tools (= 4:4.8.1-0ubuntu4.6) but it is not going to be installed
              Recommends: libqt4-opengl-dev (= 4:4.8.1-0ubuntu4.6) but it is not going to be installed
              Recommends: libqtwebkit-dev (>= 2.0~) but it is not going to be installed
E: Unable to correct problems, you have held broken packages.

My version is 12.04

---

