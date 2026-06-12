---
title: "Open Gl errors compiz and 3d chess"
date: 2007-12-07
forum: General Help
---

### Post by jediryan123 on 2007-12-07
Hi Everybody,

I installed unbuntu last night and it works perfectly except for the copiz fusion effects it says I can't use it and when I play 3d chess it says I need, open gl python bindings and gtkglext python bindings I know a guy posted about the chess a couple of months ago but no one gave him an answer, help would be much appreciated

---

### Post by psyguy1 on 2007-12-07
Python opengl bindings are easy to add, you just grab
```
sudo apt-get install python-opengl
```
I'm not sure about gtkglext (I'm still a novice) but it looks like
```
sudo apt-get install libgtkglext1
```
would be what you want for gtkglext.

Hope that helps a little bit.

---

### Post by jediryan123 on 2007-12-07
Well they seemed to install but it still doesn't work linux is hopeless I can't even play a game of chess without being spammed by error messages:( i'm running it on virtualistion so that might be the problem.

---

### Post by cojafoji on 2008-05-23
hey man, I had the same problem, and I found that you have to install the gtkglext python bindings. go into synaptic and just search for python-gtkglext1 and it'll come up. install it and it'll work like a charm.

---

### Post by breeze4you on 2008-06-05
> hey man, I had the same problem, and I found that you have to install the gtkglext python bindings. go into synaptic and just search for python-gtkglext1 and it'll come up. install it and it'll work like a charm.

Thanks man that really does it,,

---

