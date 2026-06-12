---
title: "octave-forge in hardy"
date: 2008-04-29
forum: General Help
---

### Post by theconley on 2008-04-29
There is no octave-forge in Hardy Heron.  Does anyone know if there is an Ubuntu-esque way of installing it (IE: a repo somewhere, with a .deb)?

---

### Post by alexroat on 2008-04-30
Hi,
I'm trying to build octave-forge from official release.
Considering that packages are many I&#8216;ve chosen the bundle that is available from official site through sourceforge.
I realized that it is not possible to build the last bundle with > pkg install * because it requires version 3.0.1 of octave so I downloaded from sourceforge the > octave-forge-bundle-20080216.tar.gz.
After decompression you have to move into directory and then into "main" folder and lauch "pkg install *".
Unluckily, after some warning the compilation exits with message :
> error: called from `pkg:configure_make' in file /usr/share/octave/3.0.0/m/pkg/pkg.m near line 1058, column 2
Actually I'm waiting that ubuntu team provides a packaged version of octave-forge in deb format.
PS: it seems that there are also some problems in zooming with mouse button.

Alex

---

### Post by run4flat on 2008-06-05
@theconley
Over a month later and they still don't have that out.  I wonder if it's ever going to happen.  If not, you can do what axelroat did: download the desired packages and install them manually using the package installer.  If I know more about debian package management, I might try to get this working myself, but I don't.  However...

@axelroat
I had the exact same problem you had trying to compile just the io package (I need dlmread/dlmwrite).  Apparently you need the `headers':
```
sudo apt-get install octave3.0-headers
```
Then call the same command and hopefully it will work.

As for the mouse zooming, that feature has been removed for some stupid reason having to do with gnuplot or something.  I don't remember exactly.  I hope they get that fixed soon.

For everybody else out there, if there's something you need from octave-forge, you can go to [http://octave.sourceforge.net/packages.html](http://octave.sourceforge.net/packages.html) and download each and every one you want!  I suppose they're trying to prevent code bloat.  If there's a particular function you seek, try searching for it under the function reference: [http://octave.sourceforge.net/doc/index.html](http://octave.sourceforge.net/doc/index.html).  Once you've found the function, you should be able to find the function's package and then you know what to download.

Hope that helps!

---

### Post by Telescope_Nerd on 2008-07-22
Just posted this message on a similar thread:

Just to let you know.... Although there is no Octave forge package in the repositories of hardy .deb files for most of the packages are available here:

[http://packages.ubuntu.com/intrepid/math/](http://packages.ubuntu.com/intrepid/math/)

Installing the packages this way is useful because the debian installer helps you to satisfy any missing dependencies (e.g. with odepkg)

Hope that helps

T

---

### Post by kvutza on 2008-07-22
The message about */usr/share/octave/3.0.0/m/pkg/pkg.m near line 1058, column 2* can tell more if the function **error** there is coppied into **printf** function just before it.

Some octave-forge packages do miss **-fPIC** option for **CFLAGS**, (necessary for 64bits) and it triggers the error message at some cases.

---

