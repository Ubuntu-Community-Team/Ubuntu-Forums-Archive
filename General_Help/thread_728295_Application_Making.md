---
title: "Application Making"
date: 2008-03-18
forum: General Help
---

### Post by psychofish25 on 2008-03-18
I know in windows you can compile an exe file and run that, but what would be the equivalent on ubuntu? I'm trying to write a GUI app that will run on all linux machines. Would I use python to do this?

---

### Post by scragar on 2008-03-18
you could use almost any programing language(C/C++, perl, Python being most common), you would proberly want to look into GTK if your learning perl or C/C++ though, since that's the most common method of producing windows in them, unsure about python, although it's a very popular language with ubuntu.

---

### Post by ibuclaw on 2008-03-18
As far as I'm aware, python can be run in linux from the .py scripts "as is". In other words, no compiling is required.

Though you can compile it, but the downside is that the binary would only be compatible with the version of python you used to compile it. (ie: previous and superseded versions won't work with your compiled program.)

Alternately, if you want your source hidden, there's a method called "freezing" that encrypts the file, yet still allows it to be run.

```
 apt-get install python2.5-examples 
```
And to make sure it is there.
```
 dpkg -S freeze.py 
```
Should yield a freeze.py and makefreeze.py

Iain

---

### Post by psychofish25 on 2008-03-18
Oh okay, I wasn't sure if everyone had Python though. I am already proficient in Python, I just wasn't sure whether or not I needed to compile it. But, I know how to make forms and all that jazz so I'm good for now. But one last question... when I run an application...what file format is that in?

---

