---
title: "how to install gtk+"
date: 2006-10-28
forum: General Help
---

### Post by tesseract420 on 2006-10-28
How do I install gtk? I'm getting the following error message?

$: g++ -o editor main.cpp `pkg-config --cflags gtk+-2.0` `pkg-config --libs gtk+-2.0`

Package gtk+-2.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `gtk+-2.0.pc'
to the PKG_CONFIG_PATH environment variable
No package 'gtk+-2.0' found
Package gtk+-2.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `gtk+-2.0.pc'
to the PKG_CONFIG_PATH environment variable
No package 'gtk+-2.0' found
bash: g++: command not found


Any suggestions?

Thanks.

---

### Post by SpottedOwl on 2006-10-31
I am having a similar issue with trying to build GTK for use with wxWidgets.  I have built 2.12 and, I believe, installed it, but when attempting to build wx, I get pkg-config --modversion glib-2.0 returned 2.12.0, but GLIB (2.10.3) was found!  If pkg-config was correct, then it is best to remove the old version of Glib..."

The build only requires GTK2.5 or greater, so if 2.10 is installed, why did it complain?

---

### Post by nikhilk on 2006-10-31
bash: g++: command not found

This is the last line of the output you pasted. Are you sure you have "build-essential" installed?

---

