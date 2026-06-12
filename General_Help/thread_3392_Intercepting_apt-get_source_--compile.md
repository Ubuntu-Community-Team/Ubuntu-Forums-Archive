---
title: "Intercepting apt-get source --compile???"
date: 2004-11-05
forum: General Help
---

### Post by salmankhilji on 2004-11-05
How does one have apt-get do the following?

1) download the source of a package
2) unpack the source and apply patches
3) run ./configure
4) stop and let me make a change to the source code
5) continue with the make step
6) build deb files.

Here is what I tried:

sudo apt-get source --compile libfreetype6

This performed all 6 steps above and did not let me intercept at step 4.  So here is what I tried next:

1) sudo apt-get source libfreetype6
2) cd into freetype-2.1.7
3) dpkg-buildpackage

dpkg runs and builds me .deb files.  Now I make a change to a source file and issue the dpkg-buildpackage command again.  dpkg-buildpackage starts fresh from unpacking the source stage and overrides my changes!!!

So bottom-line...I want to tell apt-get---hey stop before you start make....I want to modify the source.....okay now, you may proceed.

(I am asking this question for future reference only....I wanted to enable the byte-code interpreter in freetype and I noticed that it is already enabled!)

---

