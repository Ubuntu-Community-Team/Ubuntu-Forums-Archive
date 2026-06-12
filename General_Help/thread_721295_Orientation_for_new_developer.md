---
title: "Orientation for new developer"
date: 2008-03-11
forum: General Help
---

### Post by dmendizabal on 2008-03-11
I need to have some clarification about where to start to make my software in Linux/Ubuntu. 

I've been researching Gnome.org and the tons of documentation they provide, but I'm still lost.

I understand the concept for the Gnome architecture and the many libraries that create the whole system: GTK++, GDK, GLib, GConf, etc.
Then I read about gtkmm that seems to be Gnome/GTK++ binded for C++.

But I need the following:
1) A good IDE with UI support to make my life easy. I was used to using Eclipse on Windows and I wonder if I can continue using it. I didn't have to worry to create makefiles or to memorize lot of command line parameters to compile. It was done automatically by Eclipse and the parameters were easy to assign using dialogs.
The IDE should include the editor, debugger, tool to create dialogs (probably using the assistance of Glade), etc.

2) I would like to get a C++ programming environment. It means that all the GTK++ for instance would be completely object orient.

3) Clear and complete help for the API.


Is there a package to download from the repositories that can give me exactly what I need?
Please give me some hints.

---

### Post by justleen on 2008-03-11
Eclipse is in the repro's

im not sure about C++, i dont use that my self..

the API docs for what do you need?? gtk?

---

### Post by dmendizabal on 2008-03-17
Which one is a better alternative from the repository? Eclipse or gnome-devel?

---

### Post by jespdj on 2008-03-17
Look at the stickies in the [Programming Talk](http://ubuntuforums.org/forumdisplay.php?f=39) forum (where this question belongs).

To install the basics for compiling software (in C or C++), install build-essential:
```
sudo apt-get install build-essential
```

---

### Post by nick_h on 2008-03-17
Eclipse is good especially if you have used it before.

To install type:
```
sudo apt-get install eclipse
```

---

