---
title: "&lt;gtk/gtk.h&gt;  not found"
date: 2008-06-12
forum: General Help
---

### Post by Black Mage on 2008-06-12
In Ubuntu I have already installed the build-essentials and then I installed the gtklib2.0-dev and when I try to run a program with

#include <gtk/gtk.h>

it says

testprogram.c:1:21: error: gtk/gtk.h: No such file or directory

and a whereis gtk gives me

gtk: /etc/gtk

So what can I do to fix this? And I am relatively new to C/C++.

---

### Post by Brucevdk on 2008-06-15
> **Black Mage said:**
> So what can I do to fix this? And I am relatively new to C/C++.

I hope you're using a tutorial of some sort, such as the [GTK+ 2.0 Tutorial]() from the GNOME Documentation Library (assuming you're using C). The example there uses *pkg-config* to set the appropriate flags:
```
gcc base.c -o base `pkg-config --cflags --libs gtk+-2.0`
```

For an explanation see [Compiling Hello World](http://library.gnome.org/devel/gtk-tutorial/stable/x111.html) from the before mentioned tutorial.

You might also want to look into Python in combination with Glade (and the associated user interface designer). See [ Creating a GUI using PyGTK and Glade](http://www.learningpython.com/2006/05/07/creating-a-gui-using-pygtk-and-glade/) and the [other tutorials from Learning Python](http://www.learningpython.com/tutorial-index/).

P.S.

There's no reason to be using the *whereis* command in this situation

---

### Post by Brucevdk on 2008-06-18
[Thanks for cross posting!]("http://ubuntuforums.org/showthread.php?t=827954") </sarcasm>

---

