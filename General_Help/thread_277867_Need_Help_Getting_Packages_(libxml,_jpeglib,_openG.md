---
title: "Need Help Getting Packages (libxml, jpeglib, openGL 3D Library, GTK Library))"
date: 2006-10-15
forum: General Help
---

### Post by SendDerek on 2006-10-15
Okay, so basically I really need help with this.  I've been using Suse 10.1 for a while and decided it was buggin' out too much so I've installed a brand new clean version of kubuntu.  

I noticed that xscreensaver was either not installed or not working properly so I wanted to download the tarbar and compile/install it myself.  Only, I'm getting caught up right here:

```

#################################################################

    Warning: GTK version 2.8.20 was found, but at least one supporting
             library (libxml-2.0) was not, so GTK can't be used.
             Perhaps some of the development packages are not installed?

    Warning: The GTK libraries do not seem to be available; the
             `xscreensaver-demo' program requires them.

       Note: The JPEG library was not found.
             This means the `webcollage' program will be much slower.

       Note: The OpenGL 3D library was not found.

             Those demos which use 3D will not be built or installed.
             You might want to consider installing OpenGL and
             re-running configure.  If your vendor doesn't ship
             their own implementation of OpenGL, you can get a free
             version at <http://www.mesa3d.org/>.  For general OpenGL
             info, see <http://www.opengl.org/>.

    #################################################################

```

I'm brand new at the apt-get or the aptitude install stuff, so I don't now how to do any of it.

I need some sort of idiot-proof way of getting these library packages installed:

* libxml (the latest version of libxml)
* jpeglib
* OpenGL 3D
* GTK libraries

I know this is a lot to ask, but could somebody please help me?] (*,)

---

### Post by lamego on 2006-10-15
xscreensaver is available on the repositories... 

Anyway you can find the libs packages, example:
```
apt-cache search libxml dev
```

---

