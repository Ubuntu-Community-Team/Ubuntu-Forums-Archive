---
title: "install more than one version of GTK"
date: 2014-10-20
forum: General Help
---

### Post by pXDLQex on 2014-10-20
Hi,

I'm trying to install the package Rgtk2 in R, the statistics programme, but am unable to because Rgtk2 requires GTK version 2.8 and I have GTK version 3.0 installed (which is what came ready installed with ubuntu 14.04).

Is it possible to have more than one version of GTK installed?
If so, how would I go about installing a second version?
Would the Rgtk2 package I'm interested in automatically find the correct version or would I need to tell it where to locate the second GTK?

---

### Post by vasa1 on 2014-10-20
Did you look at [http://stackoverflow.com/questions/15868860/r-3-0-and-gtk-rgtk2-error](http://stackoverflow.com/questions/15868860/r-3-0-and-gtk-rgtk2-error) and  [https://gist.github.com/sebkopf/9405675](https://gist.github.com/sebkopf/9405675) ?

No idea whether it will work or not.

---

### Post by pXDLQex on 2014-10-21
Thanks for the links but both of them are referring to problems with GTK on other architectures (Mac and Windows) - not applicable in my case.

---

### Post by mc4man on 2014-10-21
Ubuntu includes both gtk+3.0 & gtk+2.0 (2.24),  which certainly is above 2.8 for gtk+2.0
If what you are 'installing' needs compilation then look at installing the gtk2 dev packages, libgtk2.0-dev ect.

---

### Post by pXDLQex on 2014-10-21
Thanks mc4man. I've been looking in synaptic but I only see packages related to libgtk-3-*. Do I need to add a repository to get GTK+2.0? And is it just a case of installing the libgtk-2 packages alongside the libgtk-3 packages?

---

### Post by mc4man on 2014-10-21
> **pXDLQex said:**
> Thanks mc4man. I've been looking in synaptic but I only see packages related to libgtk-3-*. Do I need to add a repository to get GTK+2.0? And is it just a case of installing the libgtk-2 packages alongside the libgtk-3 packages?

Not at all, scroll down further in synaptic or just search libgtk2

---

### Post by pXDLQex on 2014-10-22
Yes! Now it works. It was just the dev package that was missing. Thanks once again!

---

