---
title: "Can someone help decipher this terminal output?"
date: 2006-10-15
forum: General Help
---

### Post by randell6564 on 2006-10-15
Hey Folks!
I'm trying to convert and install the LimeWire.rpm.
I entered the following at the terminal to convert: ```
sudo alien LimeWireLinux.rpm
```and I got this error:> Package build failed. Here's the log:
dh_testdir
dh_testdir
dh_testroot
dh_clean -k -d
dh_installdirs
dh_installdocs
dh_installchangelogs
find . -maxdepth 1 -mindepth 1 -not -name debian -print0 | \
                xargs -0 -r -i cp -a {} debian/limewire-free
dh_compress
dh_makeshlibs
dh_installdeb
dh_shlibdeps
dpkg-shlibdeps: warning: unable to find dependency information for shared library libXt (soname 6, path /usr/lib32/libXt.so.6, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libX11 (soname 6, path /usr/lib32/libX11.so.6, dependency field Depends)
dh_gencontrol
dpkg-gencontrol: error: current build architecture amd64 does not appear in package's list (i386)
dh_gencontrol: command returned error code 65280
make: *** [binary-arch] Error 1
find: LimeWire-free-4.12.6: No such file or directory
Any ideas? Thanks!

---

### Post by kingjere on 2006-10-15
Thats the hard way. Go back and get the one for linux other.
If I remember right all you have to do is:
```

cd ~
unzip /path/to/that/limewire/file.zip
```

and to run it

```
cd /path/to/limewire/folder/
```
```
./runlime.sh
```

P.S. I'm not saying that what your doing can't be done, but thats like going around a mountain that already has a tunnel straight through it.

---

### Post by taurus on 2006-10-15
Instead of using LimeWire, why not use the free version of it called FrostWire!  You can either install it with aptitude or just download the Ubuntu/Debian version and install it from a terminal with the dpkg -i command...

[http://www.frostwire.com/](http://www.frostwire.com/)

---

### Post by randell6564 on 2006-10-15
> **kingjere said:**
> Thats the hard way. Go back and get the one for linux other.
If I remember right all you have to do is:
```

cd ~
unzip /path/to/that/limewire/file.zip
```

and to run it

```
cd /path/to/limewire/folder/
```
```
./runlime.sh
```

P.S. I'm not saying that what your doing can't be done, but thats like going around a mountain that already has a tunnel straight through it.
Hey Thanks My Friend! I did not relize that ther was another way of doing it!
It's strange though.,I have always been successful at installing the .rpm in the past! 
I noticed something in my previous post; this error:> dpkg-gencontrol: error: current build architecture amd64 does not appear in package's list (i386), that leads me to think that the failure has something to do with the fact that this time, I installed the 64-bit Ubuntu.
All of my past installations were done using the 32-bit version. Ya think I'm on to something?
Thanks again!

---

### Post by randell6564 on 2006-10-15
> **taurus said:**
> Instead of using LimeWire, why not use the free version of it called FrostWire!  You can either install it with aptitude or just download the Ubuntu/Debian version and install it from a terminal with the dpkg -i command...

[http://www.frostwire.com/](http://www.frostwire.com/)
Yeah, thats what I did! I'm using 'FrostWire' at the moment, but I paid for 'LimeWire Pro' which is faster, so I want to get what I paid for ya know?
Thanks!

---

### Post by randell6564 on 2006-10-15
kingjere, Your the Man! I got my LimeWire using the "other.zip"
Thanks again!  You have earned your way into my personal 'Man Pages'! lol!
See ya!

---

