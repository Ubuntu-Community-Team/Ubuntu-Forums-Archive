---
title: "Mathematica 5.2 no backspace or delete"
date: 2007-06-27
forum: General Help
---

### Post by Mr. Mouse on 2007-06-27
I'm not sure if this is posted in the right forum but here goes.

I am running Mathematica 5.2 on Ubuntu (it's Feisty Fawn but can't think of the version number off hand). I have installed the program no problem and started to use it, however I have run into a problem. 

[COLOR="MediumTurquoise"]Every time I hit the backspace or delete button I get a small box in place of a character or the intended deletion of characters, I was wandering if anyone else has had a similar problem and how (/if) they managed to fix it. [/COLOR]

It's important that I get his working as it is the main maths package that I have used for college and I have a lot of scripts already stored up for it that I can't readily replace if i need to g to a new system.

If all else fails is it possible to run the program in the shell and not bother with the Mathematica Front End at all?

---

### Post by Rui Pais on 2007-06-27
Hi.
Usually an elementary solution is simply... turn NumLock off.

If you find that annoying, check this:
[http://support.wolfram.com/mathematica/systems/linux/general/configurenumlock.html](http://support.wolfram.com/mathematica/systems/linux/general/configurenumlock.html)

to solve definitely the issue.

good luck.

---

### Post by Mr. Mouse on 2007-06-27
Thanks for the help. That sorted that out... odd thing that.

---

### Post by Rui Pais on 2007-06-27
yep.
That kind of keys use to give problems with *nix systems, Linux not an exception...
Until very recenty one have to install an application to enable NumLock and manually turn it on. 
With light DE (all except gnome and kde), it's still that the way. Usually console still have it disable too.

Anyway, glad you got it work :)

btw, about your other question, to run Mathematica without the front end, just run 
```
math
``` from a terminal :D

have fun

---

