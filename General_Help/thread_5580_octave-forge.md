---
title: "octave-forge"
date: 2004-11-20
forum: General Help
---

### Post by mahalram on 2004-11-20
has anyone successfully installed octave-forge by apt-getting?

apt-get install octave-forge returns with package not found...

---

### Post by TravisNewman on 2004-11-20
You have to enable universe/multiverse to get it. See the HOWTO section of the forusm.

---

### Post by mahalram on 2004-11-20
[QUOTE=panickedthumb]You have to enable universe/multiverse to get it. See the HOWTO section of the forusm.[/QUOTE]

Already done that - I've  installed quite a bit for multiverse and universe

I also filed a bug report, - for which I got a response too.

I was told there were some problems in building octave-forge, but they were corrected as of 11 Nov. 

But still no joy :(



Has anyone actually managed to install octave-forge?

---

### Post by BennBuntu on 2008-05-12
maybe 4 years too late :)

I'm on Hardy Herron using octave 3.0

I installed octave3.0-headers from the repositories,
then open up octave, cd to the source download and type

pkg install package_file_name.tar.gz

---

### Post by uve on 2008-05-23
> **BennBuntu said:**
> maybe 4 years too late :)

I'm on Hardy Herron using octave 3.0

I installed octave3.0-headers from the repositories,
then open up octave, cd to the source download and type

pkg install package_file_name.tar.gz

There was an octave-forge package in the repositories until hardy herron. Do I have to install every single package in the way you wrote?

---

### Post by jonlemur on 2008-07-02
If it's not too late, you may be able to use 

```
pkg install *.tar.gz
```

I haven't tried this, so I don't know if it will work.

---

### Post by Telescope_Nerd on 2008-07-22
Just to let you know.... Although there is no Octave forge package in the repositories of hardy .deb files for most of the packages are available here:

[http://packages.ubuntu.com/intrepid/math/](http://packages.ubuntu.com/intrepid/math/)

Installing the packages this way is useful because the debian installer helps you to satisfy any missing dependencies (e.g. with odepkg) 

Hope that helps

T

---

