---
title: "installing zsnes.. installation error"
date: 2007-06-25
forum: General Help
---

### Post by aalr1986 on 2007-06-25
hey guys.
So I go to the src directory, and type ./configure, and this is what I get:

(...a lot of things before this, but at the end these are the errors)
checking for initscr in -lcurses... no
checking for initscr in -lncurses... no
checking for initscr in -lpdcurses... no
configure: error: A curses library is required to use the debugger

any ideas of what I should do here, or what packages I need to download?!?

btw I'm using Kubuntu Fesity Fawn.

Thanks for your support!

---

### Post by Sandlst on 2007-06-25
Just wondering, is there some reason you don't want to use the package in the repository?  If this is not the case, you can install with ```
sudo apt-get install zsnes
```If you really want to install from source try searching for the packages it says you are missing, in synaptic package manager or with the code```
sudo apt-cache search PACKAGE NAME
```Good luck, post back if you have any problems!

EDIT: if you still are having trouble, maybe check out this post?
[http://ubuntuforums.org/showthread.php?t=469401](http://ubuntuforums.org/showthread.php?t=469401)

---

### Post by aalr1986 on 2007-06-25
very awesome!!!!
I got it to work...

but now it runs SUPER slow.... I mean, I have an integrated video card, with no OpenGL....

I think there's nothing I can do there but to buy a new video card....

but thanks for ur support!!! if there's something I can do here, please msg me!!

thanks again!

---

