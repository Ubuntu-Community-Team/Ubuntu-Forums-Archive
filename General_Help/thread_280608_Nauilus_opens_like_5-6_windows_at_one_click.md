---
title: "Nauilus opens like 5-6 windows at one click"
date: 2006-10-19
forum: General Help
---

### Post by mucha on 2006-10-19
I got a strange error. I click on one of my harddrives/places at the places-menu in gnome-panel. Every other time nautilus opens like 5 windows or more. One with the place has the place I wanted to go to, and the rest is in homefolder.

Anyone else that got this?

---

### Post by mucha on 2006-10-21
Did a strace and found this
```
getcwd("/home/simon", 4098)             = 12
getcwd("/home/simon", 4098)             = 12
getcwd("/home/simon", 4098)             = 12
getcwd("/home/simon", 4098)             = 12
getcwd("/home/simon", 4098)             = 12
getcwd("/home/simon", 4098)             = 12
getcwd("/home/simon", 4098)             = 12
getcwd("/home/simon", 4098)             = 12
getcwd("/home/simon", 4098)             = 12
getcwd("/home/simon", 4098)             = 12
getcwd("/home/simon", 4098)             = 12
getcwd("/home/simon", 4098)             = 12
getcwd("/home/simon", 4098)             = 12
getcwd("/home/simon", 4098)             = 12
getcwd("/home/simon", 4098)             = 12
getcwd("/home/simon", 4098)             = 12
getcwd("/home/simon", 4098)             = 12
getcwd("/home/simon", 4098)             = 12
```

Maybe this has something to do with it?

I forgot to say that I did'nt have this problem before I upgraded to Edgy.

---

### Post by mucha on 2006-10-24
Anyone? This is really annoying

---

### Post by sefs on 2006-10-24
Hey are you using an optical mouse?  It could be due to a faulty optical mouse.

I had a similar experince ... it was a newish mouse too...just a couple of weeks old but it showed its faultyness in firefox.  i would click on fire fox and it would crash...what was happening is someone one click was generating so many clicks at such a fast rate ...multipe instances of firefox were being opened and crashing.  I switched the mouse and everything went back to normal.  Would never have guessed it was the mouse it being only a few weeks old.

I now use the same fautly mouse on an xubuntu machine and if i click on thundar (nautilus opposite number in xfce) it opens multipe windows.

So... in short try a different mouse and see what happens.

Thanks.

---

### Post by mucha on 2006-10-25
Thanks for your answer. But the thing is that I tested to start nautilus from the terminal and the same happens there. Only using the keyboard

---

### Post by mucha on 2006-10-26
Well I post the whole strace if that helps to find whats wrong.
[http://www.astmatic.net/strace.out](http://www.astmatic.net/strace.out)

Ok, it seems like the only way to prevent this from happening is to already have an instance of nautilus running. Before I had the desktop-option in nautilus disabled. But now it works fine with that enabled. It would be nice though to have it normal without the desktop-option.

---

