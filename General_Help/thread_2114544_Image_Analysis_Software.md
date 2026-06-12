---
title: "Image Analysis Software"
date: 2013-02-10
forum: General Help
---

### Post by DeanoCYM on 2013-02-10
Hello all,

I'm looking to find some image analysis software on Ubuntu. I need to measure and log the diameter and coordinates of certain features on a micrograph.  [COLOR="navy"]_[300x212[ekm].jpg"]Here's a reduced example]("http://www.craftdepartment.com/ekmps/shops/craftdepartment/images/kunin-fancifelt-sheet-random-dots-white-3856-p[ekm)_[/COLOR]. 

I then need to be able to export this data so that I can use it to generate [COLOR="Navy"]_[a graph similar to this one]("http://ars.els-cdn.com/content/image/1-s2.0-S0378112704006966-gr8.jpg")._[/COLOR]

I know how to analyse the data (I use the spatstat package in r for anyone interested), but it is finding a less time consuming way to measure and export locations and size that I am finding hard to do.

I have tried using paths in the GIMP, but it exports in a horrendous half xml half csv format with a few random letters thrown in. Any better ideas?

Thanks,

Rhys

---

### Post by tgalati4 on 2013-02-10
Nothing when searching the repositories for pattern recognition, but I did find a few hits for machine vision:

tgalati4@Mint14-Extensa ~ $ apt-cache search machine vision

libopencv-ml-dev - development files for libopencv-ml
libopencv-ml2.3 - computer vision Machine Learning lib

Which leads to this wiki:

[http://opencv.willowgarage.com/wiki/](http://opencv.willowgarage.com/wiki/)

Which leads to this:

[http://opencv.org/](http://opencv.org/)

---

### Post by DeanoCYM on 2013-02-10
Thanks tgalati4, that looks perfect, I'll have a try with it tonight.

---

### Post by tgalati4 on 2013-02-10
Keep us up to date on how you solved your problem.  I'm sure you will become active on the opencv forums.

---

### Post by DeanoCYM on 2013-02-11
Certainly will do.

I can't imagine the specifics of what I am doing will be of interest to many people but... The method I am developing has its roots in Ripley's K function - a method used heavily in ecology to find evidence of clustering in trees and birds nests etc. Quite different to the engineering projects I work on - so I understand that my work could help someone that I would never expect it to.

Also I have found some more (less powerful) software that could be useful: ImageJ. This is purely image processing software and will not 'recognise' any objects.

[http://rsbweb.nih.gov/ij/docs/intro.html](http://rsbweb.nih.gov/ij/docs/intro.html)

I will have a look at them both over the next few weeks in work.

---

