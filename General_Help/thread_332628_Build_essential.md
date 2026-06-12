---
title: "Build essential"
date: 2007-01-06
forum: General Help
---

### Post by fredster001 on 2007-01-06
Hi,

I installed build-essential so i could compile C++ programs in linux. (Before you say i should move this thread, it applies to other programs as well. I did it like this:

sudo aptitude update
sudo aptitude install build-essential

it all worked fine, no errors, but when i came to open the program from the start menu, it wasnt there. I rebooted and it still isnt there. I have also tried right clicking and going to the edit menu window but it isnt in there.

Any advice for how i can get it onto the menu??


Thanks

fredster001

---

### Post by Azakus on 2007-01-06
Build-essential is not a program you use to compile with. Build-essential enables you to build a package with the dependencies you need for it to work. It doesn't do anything by itself, nor would it do any good in the menu.

---

### Post by taurus on 2007-01-06
Applications -> Accessories -> Terminal
```
gcc -v
```

---

### Post by rioghal on 2007-01-06
> **fredster001 said:**
> Hi,

I installed build-essential so i could compile C++ programs in linux. (Before you say i should move this thread, it applies to other programs as well. I did it like this:

sudo aptitude update
sudo aptitude install build-essential

it all worked fine, no errors, but when i came to open the program from the start menu, it wasnt there. I rebooted and it still isnt there. I have also tried right clicking and going to the edit menu window but it isnt in there.

Any advice for how i can get it onto the menu??


Thanks

fredster001

For a new app to show up in the gnome menus until you do one of two things.

1) Either add a new menu item using alacarte, or
2) Add a new .desktop file, for the new app, in /usr/share/applications.

Many times the developer of the app will create the menu files for you and those files will be installed when you do a 'sudo make install', but that isn't always the case. If this is an app that you wrote yourself, you'll need to create the .desktop files (menu file) yourself.

You can open the files in /usr/share/applications in a text editor and see how they are layed out. This will enable you to make your own. Usually, GUI apps that you install from a package manager already have the menu files created by either the packager or the app developer so you usually don't have to mess with menu item creation.

I'd say creating a menu item for an app that you wrote is the easiest and quickest part of adding a new app to your system.

---

### Post by fredster001 on 2007-01-06
Thanks, but i'm sorry, dont think i'm getting this.

Say i wish to write a simple program in C++. I write it in text editor, then what??

fredster001

---

### Post by taurus on 2007-01-06
```
gcc **program.cc**
-or-
cpp **program.cpp**
```

---

### Post by rioghal on 2007-01-06
> **fredster001 said:**
> Thanks, but i'm sorry, dont think i'm getting this.

Say i wish to write a simple program in C++. I write it in text editor, then what??

fredster001
I'm sorry, I thought you were talking about getting a new app, that you wrote, into the gnome menus. I misunderstood your original post, sorry.
See the above posts in reference to gcc/cpp.

---

### Post by fredster001 on 2007-01-06
ok, thanks taurus.

It works, however it ran the program in the terminal. Is there any way to get it to compile the program and save it as the linux eqivilent of a .exe file, (what is that btw)


Thanks

---

