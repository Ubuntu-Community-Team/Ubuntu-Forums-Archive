---
title: "Global Menu on Ubuntu 8.04 64-bit - Possible?"
date: 2008-06-15
forum: General Help
---

### Post by DieseL1988 on 2008-06-15
I've seen alot of the global menu on various screenshots etc. and I want to give it a try. However, I haven't found an install guide that says Ubuntu 8.04 is supported. I'm also running 64-bit just to make life a little more complicated :)

So any know if it's possible?

---

### Post by Arthur Archnix on 2008-06-15
What is a global menu? Attach a screenshot or a link if you can.

---

### Post by Forlong on 2008-06-15
As far as I know, it can't be build for 64-bit ATM.

Please correct me if I'm wrong.


@Arthur Archnix: [http://code.google.com/p/gnome2-globalmenu/](http://code.google.com/p/gnome2-globalmenu/)

---

### Post by DieseL1988 on 2008-06-15
[https://wiki.ubuntu.com/global_menu](https://wiki.ubuntu.com/global_menu)

Note the warning at the top...

EDIT: lol you beat me to it, but yeah that's the one. So it can't be done for 64? :(

---

### Post by mysticrider92 on 2008-06-15
> **DieseL1988 said:**
> EDIT: lol you beat me to it, but yeah that's the one. So it can't be done for 64? :(

It can be done. Just depends on how much time and effort you are willing to put into it. The Ubuntu install page has a few comments that outline the problems you will get. If you can fix those problems, it will be an easy install.

I think, from reading through that page, the problem is the GTK libraries it is linked to. Changing the configure script to link it to 64-bit libraries should work. The problem you will have is that the Mac menu mod won't be shown when running 32-bit apps (Ubuntu 64-bit is not pure 64-bit). 

I am tempted to try installing Ubuntu 64 to play around with, and the weather is really bad today, so I will let you know how it goes.

[edit] Decided against installing 64-bit Ubuntu, but I did stumble on this:[http://ubuntuforums.org/showthread.php?t=474790&highlight=getlibs]("http://ubuntuforums.org/showthread.php?t=474790&highlight=getlibs"). I wonder if that script could be used to install the 32-bit version of the Mac menu. It would be slightly messier than compiling it yourself, but is more likely to work right.

---

