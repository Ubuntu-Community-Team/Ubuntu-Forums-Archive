---
title: "Need appropriate *-dev package names for building tango"
date: 2007-04-05
forum: General Help
---

### Post by kpkeerthi on 2007-04-05
Referred the requirements at [http://tango.freedesktop.org/Installation](http://tango.freedesktop.org/Installation). I need     
    * GNU Automake 1.9.x 
    * ImageMagick version 5.5.7 or greater
    * pkgconfig version 0.19 or greater
    * XML::Simple Perl Module 
source packages. But I'm not sure what  dev packages I should install from the repository. 

Doing aptitude search did not reveal anything appropriate. Can someone please give me the *-dev package names for the above? Thanks,

---

### Post by RaZer0r on 2007-04-05
try using synaptic package manager, which can be found at: system, Administration
if you search closely you'll find those packages. I just call this a bit lazyness :p as my first search came up with this results:
automake (version 1.1 until 1.9, including the docs)
imagemagick
pkg-config
libxml-simple-perl
so to make a copy paste example for you

```

sudo aptitude install automake imagemagick pkg-config libxml-simple-perl

```

that should be all :)

---

