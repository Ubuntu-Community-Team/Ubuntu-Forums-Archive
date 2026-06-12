---
title: "C++ for Dummies"
date: 2007-11-19
forum: General Help
---

### Post by smd0665 on 2007-11-19
I recently bought the book "C++ for Dummies" and, of course, the program that came with the book is a Windoze program, Dev-C++. My son says the reason they included a Windoze program is because it's for dummies! Anyway, I've heard I could use Anjuta or KDevelop instead, but I haven't found a way to create an executable with either of these programs. Does anyone know how to do that?

---

### Post by vambo on 2007-11-19
This might be worth reading prior to diving in.
[http://ubuntuforums.org/showthread.php?t=554070]("http://ubuntuforums.org/showthread.php?t=554070")

---

### Post by smd0665 on 2007-11-22
Well, after playing around with KDevelop and Anjuta, and even installing Dev-C++ on my other computer (running XP), I finally got it to work. Here's what I did, in case someone else has this question again: key the program into Emacs. To compile from Emacs, go up to Tools and then Compile. It will create an executable in the same file as your program.  Simple solution, but it took a while to figure it out.

---

### Post by Sockerdrickan on 2007-11-22
The coolest way to do it is to just open up a terminal and do

g++ lol.cpp

then

./a.out to launch your app

---

