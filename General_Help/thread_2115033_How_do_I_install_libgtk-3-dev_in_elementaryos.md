---
title: "How do I install libgtk-3-dev in elementaryos?"
date: 2013-02-11
forum: General Help
---

### Post by funenga on 2013-02-11
[EDIT] Forget it... I had to enable precise-updates... Sorry.


I'm trying to compile pantheon-terminal's source. In order to do that I need to install some dependencies. I'm using elementaryos, just installed it yesterday (all software is upgraded).

The source is written in Vala and one of the dependencies, is the package libgtk-3-dev.

This is what I can understand with my beginner linux knowledge base (see the outputs in the end):

[LIST]
[*]From the first command I can see that I've libgtk-3-0 3.4.2-0ubuntu0.5 installed
[*]From the second I understand the package libgtk-3-dev depends on libgtk-3-0 (= 3.4.1-0ubuntu1)
[*]libgtk-3-0 3.4.2-0ubuntu0.5 is to be installed??? what the hell is this? isnt 3.4.2-0ubuntu0.5 already installed?
[/LIST]

```
ffunenga@asus:~$ dpkg -l | grep libgtk-3
ii  libgtk-3-0                             3.4.2-0ubuntu0.5                        GTK+ graphical user interface library
ii  libgtk-3-bin                           3.4.2-0ubuntu0.5                        programs for the GTK+ graphical user interface library
ii  libgtk-3-common                        3.4.2-0ubuntu0.5                        common files for the GTK+ graphical user interface library
ffunenga@asus:~$ sudo apt-get install libgtk-3-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 libgtk-3-dev : Depends: libgtk-3-0 (= 3.4.1-0ubuntu1) but 3.4.2-0ubuntu0.5 is to be installed
                Depends: gir1.2-gtk-3.0 (= 3.4.1-0ubuntu1) but 3.4.2-0ubuntu0.5 is to be installed
                Depends: libglib2.0-dev (>= 2.32.0) but it is not going to be installed
                Depends: libgdk-pixbuf2.0-dev (>= 2.26.0) but it is not going to be installed
                Depends: libpango1.0-dev (>= 1.30.0) but it is not going to be installed
                Depends: libatk1.0-dev (>= 2.2.0) but it is not going to be installed
                Depends: libcairo2-dev (>= 1.10.0) but it is not going to be installed
                Depends: libx11-dev (>= 2:1.0.0-6) but it is not going to be installed
                Depends: libxext-dev (>= 1:1.0.1-2) but it is not going to be installed
                Depends: libxinerama-dev (>= 1:1.0.1-4.1) but it is not going to be installed
                Depends: libxi-dev (>= 1:1.0.1-4) but it is not going to be installed
                Depends: libxrandr-dev (>= 1:1.2.99) but it is not going to be installed
                Depends: libxcursor-dev but it is not going to be installed
                Depends: libxfixes-dev (>= 1:3.0.0-3) but it is not going to be installed
                Depends: libxcomposite-dev (>= 1:0.2.0-3) but it is not going to be installed
                Depends: libxdamage-dev (>= 1:1.0.1-3) but it is not going to be installed
                Recommends: debhelper but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
```

---

