---
title: "Xubuntu doesn't work with python packages"
date: 2007-05-17
forum: General Help
---

### Post by other on 2007-05-17
I'm running Xubuntu 7.04 and I can't get any of the python packages (python-gtk, python-qt etc.) to work. I can't run hp-toolbox because it can't find PyQt, and installing python-qt didn't change anything.

I can't compile Scribes, because first it couldn't find python bindings for dbus (installing python-dbus didn't do anything, but downloading dbus-python from freedesktop.org and compiling it solved that problem), then it couldn't find pygobject etc. And I can't solve these problems by installing the packages with apt. Why doesn't it work?

Also, since I installed some package "manually" (I believe it was pygobject), QuodLibet doesn't work anymore. Do I need to run Ubuntu for the packages in the repository to work?

---

### Post by Belathor on 2007-05-17
Everything but Scribes should be available from the repositories. They are just oddly named. ie: dbus-python is python-dbus, pygobject is python-gobject.

---

### Post by other on 2007-05-17
Yes, I know. I said that in my post. But installing, for example, python-dbus, doesn't work. After installing it, I still can't run "import dbus" in python. Something is wrong. I merely mentioned Scribes as an example that won't compile, because the packages in the repositories doesn't work.

Is this because I'm running Xubuntu? Because I didn't have this problem with Ubuntu. I don't understand why the packages wouldn't work though, regardless of what DE I'm using.

---

