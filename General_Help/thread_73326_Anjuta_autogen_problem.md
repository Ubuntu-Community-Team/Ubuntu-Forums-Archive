---
title: "Anjuta autogen problem"
date: 2005-10-08
forum: General Help
---

### Post by redbull on 2005-10-08
I want to play around with C programming, so I installed the Anjuta IDE with Synaptic. If I try to use the application wizard to write the "Hello World" program, my screen looks like this: (screen shots attached)

(I couldn't copy/paste from the window for some reason)

---

### Post by cpscotti on 2005-10-09
Hey, I have exactly the same problem!

anyone knows how to solve it &#322;

---

### Post by Comrade on 2005-10-09
I also have this problem. I checked, and I have autoconf installed.

---

### Post by redbull on 2005-10-11
Anyone have Anjuta actually working?

---

### Post by Comrade on 2005-10-13
Part of the problem is not having libtool installed. But still, autogen.sh is not working.

---

### Post by cpscotti on 2005-10-22
now my Anjuta is working, my problem seems to be:
g++
try it!

---

### Post by Comrade on 2005-10-22
I don't understand. Did you need to install g++, or was something not configured properly?

---

### Post by cpscotti on 2005-11-29
I needed to install g++, just this, 
After that, everything went ok!

(g++ is not on the "required" list for anjuta)

---

