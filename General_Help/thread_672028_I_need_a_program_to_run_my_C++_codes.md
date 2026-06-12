---
title: "I need a program to run my C++ codes"
date: 2008-01-19
forum: General Help
---

### Post by ayet on 2008-01-19
I am student and we are into C++ but in school its in windows, I Need help on what program to use on Ubuntu to run my C++ codes at home. tnks.

---

### Post by TheLions on 2008-01-19
try kdevelop

---

### Post by heindsight on 2008-01-19
Depends on what you want. If you just want a compiler to compile your C++ code so that you can run it, then install the gcc and g++ packages and all their dependencies and recommended and suggested packages. Then you can use the g++ command to compile your code.

If you're looking for an IDE from which you can edit, debug, compile and run your code, then kdevelop is certainly an option, but you could also try anjuta or eclipse with the eclipse-cdt package.

---

### Post by ayet on 2008-01-19
aside from Kdevelop is there other programs?

---

### Post by nick_h on 2008-01-19
If you just need command line tools then install the build-essential package with:
```
sudo apt-get install build-essential
```
If you are looking for an IDE read the [ What's your Favorite IDE?](http://ubuntuforums.org/showthread.php?t=6762) thread in the [Programming Talk](http://ubuntuforums.org/forumdisplay.php?f=39) section.

---

### Post by leg on 2008-01-19
Just make sure that any programs you bring home don't rely on the win32 api. If you create your projects in studio 2005 for instance by default your programs are pulling a lot of windows libs which you won't have on a Linux box. You could run your program through wine or you could use a linux IDE and rewrite which will re-inforce the techniques you are learning. The IDE I would suggest would be code::blocks. I think this is a very nice environment to be using. There is also Anjuta and kdevelop. I personally did not like Kdevelop very much but you will have to try them for yourself.

---

### Post by Xanderfoxx on 2008-01-19
> **ayet said:**
> [A]side from Kdevelop [are] there other programs?

Well, let's see...

In Ubuntu, besides KDevelop, there is:
[LIST=1]
[*]Eclipse
[*]gcc & g++
[*]Mono
[*]Emacs
[*]Kate
[*]Medit
[*]Motor
[*]Vim[/LIST]

---

### Post by Lord Illidan on 2008-01-19
Or Geany, pretty nice and small.

---

### Post by Xanderfoxx on 2008-01-22
I've never heard of that one. Is it in the repos?

Tell us about it! [speaks in eager tone]

---

### Post by x001 on 2008-01-22
I use geany as well for my C++ class. Works great and it is available via the repos.

---

### Post by Lord Illidan on 2008-01-23
> **maurin.alex@gmail.com said:**
> I've never heard of that one. Is it in the repos?

Tell us about it! [speaks in eager tone] It wouldn't kill you to search for it in synaptic.

---

