---
title: "What's the VB6 equilivent in Ubuntu?"
date: 2007-11-17
forum: General Help
---

### Post by hopelessone on 2007-11-17
Hi all,

its been a few months now since i moved from Windoze.. how can i make a GUI face? i mean click to add buttons, resize windows, add text inputs...etc...

i tried looking in programming but don't ave a clue where to start...

all help appreciated..

thanks..

---

### Post by HankB on 2007-11-17
You've touched on one of the areas where Linux lags, at least the last time I looked. You might try googling for "Linux GUI builder" and follow some of the links.

One that looks promising is Glade. I see it has bindings for Perl (amongst others.) Perl is  like VB in that it is interpreted. One of the strengths of Perl is the plethora of packages. (see CPAN.) It seems like there is a package for almost anything. When you get to the back end - actually doing something with the GUI - Perl is pretty powerful. But that power comes at a price. Perl can be difficult fathom at times.

Another highly popular language with which I am less familiar is Python. If you're learning from scratch, that might be a better choice due to it's true object orientation. Search for "python GUI builder" and see what hits you come up with.

It's been a long time since I looked at this subject. Maybe Linux is no longer lagging.

HTH,
hank

---

### Post by Rui Pais on 2007-11-17
> **hopelessone said:**
> Hi all,

its been a few months now since i moved from Windoze.. how can i make a GUI face? i mean click to add buttons, resize windows, add text inputs...etc...

i tried looking in programming but don't ave a clue where to start...

all help appreciated..

thanks..

Hi,
Python is a good suggestions. 
For script gui interfaces you can try zenity too, it's simple.

For something really like VB try:
```
sudo apt-get install gambas2
```
:)

---

### Post by Majorix on 2007-12-01
Hi.

I had never heard of Gambas. I am installing it now, will have a look. Thanks.

Under Linux the best way to program GUI's is by using a RAD like wxGlade, Glade or Boa Constructor (they are like VS), along with the Python language (you can think of it like VB, although they are far apart).

---

### Post by Rui Pais on 2007-12-01
> **Majorix said:**
> Hi.

I had never heard of Gambas. I am installing it now, will have a look. Thanks.

Under Linux the best way to program GUI's is by using a RAD like wxGlade, Glade or Boa Constructor (they are like VS), along with the Python language (you can think of it like VB, although they are far apart).

You welcome. 
The advantage of gambas, for a VB user, it's the syntax that it's very similar. 
I don't tried for quiet a long time, but they even include a wizard to convert simpler MSVB projects to Gambas.

---

### Post by bruce2000 on 2007-12-01
Hi,

You might also want to look at RealBasic which is free of charge to Linux users (the standard edition anyway)

I've tried both this and Gambas and found the latter to be better.. becuse RB was too sluggish/bloated on my system

[http://www.realsoftware.com/products/realbasic/index.php]("http://www.realsoftware.com/products/realbasic/index.php")

---

