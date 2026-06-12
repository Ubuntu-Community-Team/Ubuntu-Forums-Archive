---
title: "Yet another Compiz problem thread (dependency problems)"
date: 2008-07-02
forum: General Help
---

### Post by chalewa on 2008-07-02
I'm trying to install compiz from git..

but i get this error during the make of compiz


No package 'x11-xcb' found
No package 'xcomposite' found
No package 'xfixes' found
No package 'xdamage' found
No package 'xrandr' found
No package 'xinerama' found
No package 'libstartup-notification-1.0' found


any idea how to solve these package errors?

---

### Post by isaacj87 on 2008-07-02
Hey there, it would seem you are missing a lot dependencies ;)

No worries though, just run this command in terminal and you'll have all the dependencies needed to build CF from Git. :)

```
sudo apt-get install build-essential gitweb curl autoconf automake automake1.9 libtool intltool libxslt1-dev xsltproc libwnck-dev libxcomposite-dev libpng12-dev libsm-dev libxrandr-dev libxdamage-dev libxinerama-dev libstartup-notification0-dev libgconf2-dev libgl1-mesa-dev libglu1-mesa-dev libmetacity-dev librsvg2-dev libdbus-1-dev libdbus-glib-1-dev libgnome-desktop-dev libgnome-window-settings-dev python-dev python-pyrex libx11-xcb-dev
```

---

### Post by chalewa on 2008-07-03
hey thanks for your respsonse..

i tried to run that in the terminal this morning, just a moment ago actually, and ended up with this..


```
chalewa4bambu@chalewa4bambu-desktop:~$ sudo apt-get install build-essential gitweb curl autoconf automake automake1.9 libtool intltool libxslt1-dev xsltproc libwnck-dev libxcomposite-dev libpng12-dev libsm-dev libxrandr-dev libxdamage-dev libxinerama-dev libstartup-notification0-dev libgconf2-dev libgl1-mesa-dev libglu1-mesa-dev libmetacity-dev librsvg2-dev libdbus-1-dev libdbus-glib-1-dev libgnome-desktop-dev libgnome-window-settings-dev python-dev python-pyrex libx11-xcb-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
autoconf is already the newest version.
autoconf set to manually installed.
automake is already the newest version.
libtool is already the newest version.
intltool is already the newest version.
libxslt1-dev is already the newest version.
xsltproc is already the newest version.
libpng12-dev is already the newest version.
libsm-dev is already the newest version.
libgconf2-dev is already the newest version.
libdbus-1-dev is already the newest version.
libdbus-glib-1-dev is already the newest version.
libgnome-window-settings-dev is already the newest version.
python-dev is already the newest version.
python-dev set to manually installed.
python-pyrex is already the newest version.
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libgl1-mesa-dev: Depends: mesa-common-dev (= 7.0.3~rc2-1ubuntu3) but it is not going to be installed
  libgnome-desktop-dev: Depends: libgnomeui-dev (>= 2.14.1-1) but it is not going to be installed
  libmetacity-dev: Depends: libgtk2.0-dev (>= 2.10.0-1) but it is not going to be installed
  librsvg2-dev: Depends: libcairo2-dev (>= 1.2.0) but it is not going to be installed
                Depends: libgtk2.0-dev (>= 2.10.1-1) but it is not going to be installed
  libstartup-notification0-dev: Depends: libx11-dev but it is not going to be installed
  libwnck-dev: Depends: libgtk2.0-dev (>= 2.8.17-1) but it is not going to be installed
               Depends: libxres-dev but it is not going to be installed
  libx11-xcb-dev: Depends: libx11-dev but it is not going to be installed
  libxcomposite-dev: Depends: libx11-dev but it is not going to be installed
                     Depends: libxfixes-dev but it is not going to be installed
  libxdamage-dev: Depends: libx11-dev but it is not going to be installed
                  Depends: libxfixes-dev but it is not going to be installed
  libxinerama-dev: Depends: libx11-dev but it is not going to be installed
                   Depends: libxext-dev but it is not going to be installed
  libxrandr-dev: Depends: libx11-dev but it is not going to be installed
                 Depends: libxext-dev but it is not going to be installed
                 Depends: libxrender-dev but it is not going to be installed
E: Broken packages

```

---

### Post by isaacj87 on 2008-07-03
Hmm...that's strange.

What version of Ubuntu are you running? Feisty (7.04), Gutsy (7.10), Hardy (8.04)?

Try running this command and see if it clears up (I think this is the command):

```
sudo apt-get install -f
```

---

### Post by chalewa on 2008-07-04
> **isaacj87 said:**
> Hmm...that's strange.

What version of Ubuntu are you running? Feisty (7.04), Gutsy (7.10), Hardy (8.04)?

Try running this command and see if it clears up (I think this is the command):

```
sudo apt-get install -f
```

8.04

i tried running that command, didn't really seem to resolve anything, im thinking that i am going to try a fresh install or something. its like part of an xorg package somewhere along the way didn't get fully installed.

---

