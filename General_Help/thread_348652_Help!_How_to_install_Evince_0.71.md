---
title: "Help! How to install Evince 0.71?"
date: 2007-01-29
forum: General Help
---

### Post by xpan on 2007-01-29
Hi,

It seems that the version of evince that comes with ubuntu has some problems with printing (landscape printing does not work very well). So I decided to download the newest version (0.71) from the ubuntu repositories ([http://archive.ubuntu.com/ubuntu/pool/main/e/evince/)](http://archive.ubuntu.com/ubuntu/pool/main/e/evince/)).

I run the .deb package and I get the message (from dpkg) "Error: Dependency is not satisfiable: libatk1.0-0"

Why is that? 

(PS: Using ubuntu edgy eft on a i386 machine)

---

### Post by xpan on 2007-01-30
I can't understand. Does this mean that there is no way for me to install the latest evince? Or should I wait for it to appear in the apt-get repos?

---

### Post by ernstblaauw on 2007-02-22
I would also like to know this. Does someone know how to install the latest Evince (0.7.2)?

---

### Post by Athropos on 2007-02-24
Evince development is close to Gnome's one, so if you want to install a new version of Evince, you'll surely also need to update a lot of Gnome libraries.

The best thing to do is probably to wait for the Feisty release. It's a pity since the Evince version in Edgy crashes with a lot pdf files, and this crash has been fixed in recent versions. The patch will perhaps be backported one day...

---

