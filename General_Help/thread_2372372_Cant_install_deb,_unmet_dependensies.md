---
title: "Cant install deb, unmet dependensies"
date: 2017-09-24
forum: General Help
---

### Post by woodchuck2 on 2017-09-24
Hello, i have a problem, ubuntu 16.04, whenever i try to install any deb package, right now it is intel update tool i get an error - 
dpkg: error processing package intel-graphics-update-tool (--install):
 dependency problems - leaving unconfigured
Processing triggers for gnome-menus (3.13.3-6ubuntu3.1) ...
Processing triggers for desktop-file-utils (0.22-1ubuntu5.1) ...
Processing triggers for bamfdaemon (0.5.3~bzr0+16.04.20160824-0ubuntu1) ...
Rebuilding /usr/share/applications/bamf-2.index...
Processing triggers for mime-support (3.59ubuntu1) ...
Errors were encountered while processing:
 intel-graphics-update-tool

i have tried as a lot of things but i just cant get it to work

---

### Post by oldos2er on 2017-09-24
I can't find any package in the default repositories with the name "intel-graphics-update-tool." If you downloaded this from somewhere, can you provide a link? Or is it from a PPA or other external repo? 

> i have tried as a lot of things It would help if you could list what you tried, and any further error messages if they exist.

The more info you can provide, the better.

---

### Post by jeremy31 on 2017-09-24
Hi oldos2er
[https://01.org/linuxgraphics/forum/update-tool-support-forum/update-tool-2.0.2-ubuntu-16.04-cannot-update-driver-due-dependencies](https://01.org/linuxgraphics/forum/update-tool-support-forum/update-tool-2.0.2-ubuntu-16.04-cannot-update-driver-due-dependencies)
Intel likely hasn't updated anything from a year ago, as they did with Ubuntu 14.04

---

### Post by mc4man on 2017-09-24
That tool & packages it wants to install can only be used on a 16.04 or 16.04.1 image installs.
Even then if the 16.04/.1 install updated to newer mesa it may present issue. 
16.04.2/16.04.3 images would be using a HWE xserver so the Intel thing would be useless.

Generally it should just fail to install & go away when attempted on a 16.04.2/.3 image install

---

### Post by ajgreeny on 2017-09-24
How are you attempting to install the .deb?
If using ```
sudo dpkg -i intel-graphics-update-tool.deb
``` or some similar command, be warned that dpkg is hopeless at downloading and installing any dependencies; you will possibly do better with **gdebi** the GUI installer for .deb packages which you can install from the repos.

However my major first query is, why do you think you need to update your Intel graphics; do you have some difficulties or problems with the version that comes with 16.04?

---

### Post by oldos2er on 2017-09-24
> **jeremy31 said:**
> Hi oldos2er
[https://01.org/linuxgraphics/forum/update-tool-support-forum/update-tool-2.0.2-ubuntu-16.04-cannot-update-driver-due-dependencies](https://01.org/linuxgraphics/forum/update-tool-support-forum/update-tool-2.0.2-ubuntu-16.04-cannot-update-driver-due-dependencies)
Intel likely hasn't updated anything from a year ago, as they did with Ubuntu 14.04

Thanks!

---

