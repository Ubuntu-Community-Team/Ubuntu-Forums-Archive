---
title: "Cario intergration packages?"
date: 2005-04-04
forum: General Help
---

### Post by Jesus Franco on 2005-04-04
From my understanding after going to these sites...
[http://cairographics.org/](http://cairographics.org/)
[http://people.redhat.com/otaylor/guadec5/](http://people.redhat.com/otaylor/guadec5/)

And a hell of alot of webbrowsing I found several cvs tarballs to intergrate gtk with the Cairo engine.  :mrgreen: 

This allows for AMAZING rendering of themes/fonts etc.

Example
[IMG]http://www.gnome.org/~seth/blog-images/monkey-hoot/cairo-comparison.png[/IMG] 

After a bunch of errors I would like to know if anyone here has done this or knows how to do this and can Explain in what order the files need to be installed and also were to locate those files. Even better maybe someone knows a repository that has these files in it.  \\:D/ 

Thanks!  :mrgreen:

---

### Post by bored2k on 2005-04-04
/home/reb # apt-cache search libcairo1-dev
libcairo1-dev - Multi-platform 2D graphics library
/home/reb # man libcairo1
> Description: Multi-platform 2D graphics library
 Provides anti-aliased vector-based rendering for X. Paths consist
 of line segments and cubic splines and can be rendered at any width
 with various join and cap styles. All colors may be specified with
 optional translucence (opacity/alpha) and combined using the extended
 Porter/Duff compositing algebra as found in the X Render Extension. 
root@noir:/home/reb # apt-get install libcairo1-dev
Reading package lists... Done
Building dependency tree... Done
The following extra packages will be installed:
  libcairo1 libpixman1 libpixman1-dev libpng12-dev
The following NEW packages will be installed:
  libcairo1 libcairo1-dev libpixman1 libpixman1-dev libpng12-dev
0 upgraded, 5 newly installed, 0 to remove and 3 not upgraded.
Need to get 609kB of archives.
After unpacking 1663kB of additional disk space will be used.
Do you want to continue [Y/n]?

Universe Multiverse Repositories ;) .

---

### Post by Jesus Franco on 2005-04-06
Thank you very much. Every package installed successfully. It is installed but there is no difference. Everything looks the same. The color wheel looks exactly the same way it used to 'choppy' and not smooth like the preview image.  :-? 

Is there anything i need to configure for it to work?
I am currently using the fglrx drivers.

---

### Post by bored2k on 2005-04-06
> man libcairo1

That is the manual for it. That should tell you what to do. Can't help anymore because I haven't done anything with it.

---

