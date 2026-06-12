---
title: "Installing a package"
date: 2007-11-05
forum: General Help
---

### Post by the lemming on 2007-11-05
I have found something that I would like to install which is not in the synaptic package manager and I haven't got a clue what to do.

[http://sourceforge.net/project/showfiles.php?group_id=201037](http://sourceforge.net/project/showfiles.php?group_id=201037)

Its a driver for a Pantone Huey.  So far I downloaded the package and hit the extract button and from there I exhausted the limit of my knowledge because I haven't got a clue if it worked or not.

I tried to look for something without realising what I was looking for r where to look.

Could somebody please tell me if I have done anything right or wrong or where to look to find what it was that I was supposed to have installed.

I've read loads but it goes way over my head.

Sorry for being so bland.

---

### Post by Maestro23 on 2007-11-05
Installing Software in Ubuntu:
[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

*That tarball should contain a README/INSTALL doc with additional instructions/requirements.  They can be a pain for someone new to linux.  Make sure you read the documentation.

Good luck.

---

### Post by Feureau on 2007-11-14
Hi, I'm trying to do the same thing as the first user is trying to achieve.
I downloaded the package and it's actually uncompiled source code buildable using scons. It lists some libs that it needs for scons to build the thing. I'm pretty sure I got at least some of these already installed in my ubuntu box, but how do I check that I got the offending libs? If there's a libs that I don't have, where should I put them?

here's the install note included in the message that lists the libs:
> You need scons ([http://www.scons.org/](http://www.scons.org/)) to build project.
Also following libs must be installed: libXxf86vm, libusb, libsdl and ccmath ([http://freshmeat.net/projects/ccmath/](http://freshmeat.net/projects/ccmath/))
Then just type 'scons' in project directory and you'll get 'mcalib' and 'mgramp' executables.

Any help is appreciated and thank you very much. :)

---

### Post by oldos2er on 2007-11-14
You should be able to find all the dependencies you need (including scons) in Synaptic Package Manager.

---

### Post by geirha on 2007-11-15
Looks easy, but it's not ;)

First of all, you need to install those deps. All but one of them are provided by ubuntu-packages.
```
sudo aptitude install g++ scons libsdl-dev libxxf86vm-dev libusb-dev
```
Couldn't find the ccmath library in the ubuntu repositories, so you have to compile that too.
```
cd /tmp      # or some other place where you have write access

# Unpack the ccmath-source
wget http://freshmeat.net/redir/ccmath/1083/url_tgz/ccmath-2.2.1.tar.gz -O - | tar zxf -
cd ccmath-2.2.1

# Build using the provided bash script (!?) It prints a lot of warnings, but they should be
# safe to ignore.
./makelibs.sh       # You probably have intel platform :)

# Install. The provided install script doesn't work very well, so install it manually and in
# the proper place
sudo install -m 755 tmp/libccm.so /usr/local/lib/
sudo install -m 644 tmp/libccm.a /usr/local/lib/
sudo install -m 644 ccmath.h /usr/local/include/
sudo ldconfig

cd .. # Done with ccmath

```

Next, the mcalib
```

cd /tmp

# Unpack the source
wget http://garr.dl.sourceforge.net/sourceforge/mcalib/mcalib-0.0.1.tar.bz2 -O - | tar jxf -
cd mcalib-0.0.1

# Build using scons (what's wrong with make?!)
scons

# Now you have two binaries, mgramp and mcalib. Put them somewhere in your PATH
sudo install -m 755 mgramp mcalib /usr/local/bin/

```

Good luck.

---

### Post by Feureau on 2007-11-15
Hi, geirha, thanks for the wonderfully detailed explanation. :D
Although, I'm stuck, I got this when installing the libs, it asks for Gutsy CD which I put in my cd drive and load, but it keeps asking for it. It goes on like this, (this screenshot is my second try) but sometimes it will spit out some info that it's downloading stuff and after a while it just stops. 
I think it's the g++, I tried installing the sudo aptitude one by one and it seems g++, libsdl-dev and libusb-dev are the ones giving me grief.
Did I miss something?
Thanks 
[CENTER][IMG]http://img161.imageshack.us/img161/8582/screenshotbf7.png[/IMG][/CENTER]

---

### Post by geirha on 2007-11-15
Looks like it has trouble identifying the CD, so just go to System -> Administration -> Software Sources and disable the ubuntu cd.

---

### Post by Feureau on 2007-11-16
Hi, thanks for the prompt response.
Turning off the CD source fixed that problem, but I can't seem to install ccmath. 
I don't suppose it's because I'm running ubuntu 64bit on an AMD? The compile didn't seem to spit out any file(s). Though it did spit out a bunch of these:

> complex.h:23: warning: conflicting types for built-in function 'cacosh'
complex.h:23: warning: conflicting types for built-in function 'catanh'
In file included from fftgr.c:8:
complex.h:18: warning: conflicting types for built-in function 'cabs'
complex.h:19: warning: conflicting types for built-in function 'csqrt'
complex.h:19: warning: conflicting types for built-in function 'cexp'
complex.h:19: warning: conflicting types for built-in function 'clog'
complex.h:20: warning: conflicting types for built-in function 'csin'
complex.h:20: warning: conflicting types for built-in function 'ccos'
complex.h:20: warning: conflicting types for built-in function 'ctan'
complex.h:21: warning: conflicting types for built-in function 'casin'
complex.h:21: warning: conflicting types for built-in function 'cacos'
complex.h:21: warning: conflicting types for built-in function 'catan'
complex.h:22: warning: conflicting types for built-in function 'csinh'
complex.h:22: warning: conflicting types for built-in function 'ccosh'
complex.h:22: warning: conflicting types for built-in function 'ctanh'
complex.h:23: warning: conflicting types for built-in function 'casinh'
complex.h:23: warning: conflicting types for built-in function 'cacosh'
complex.h:23: warning: conflicting types for built-in function 'catanh'
In file included from pshuf.c:9:
complex.h:18: warning: conflicting types for built-in function 'cabs'
complex.h:19: warning: conflicting types for built-in function 'csqrt'
complex.h:19: warning: conflicting types for built-in function 'cexp'
complex.h:19: warning: conflicting types for built-in function 'clog'
complex.h:20: warning: conflicting types for built-in function 'csin'
complex.h:20: warning: conflicting types for built-in function 'ccos'
complex.h:20: warning: conflicting types for built-in function 'ctan'
complex.h:21: warning: conflicting types for built-in function 'casin'
complex.h:21: warning: conflicting types for built-in function 'cacos'
complex.h:21: warning: conflicting types for built-in function 'catan'
complex.h:22: warning: conflicting types for built-in function 'csinh'
complex.h:22: warning: conflicting types for built-in function 'ccosh'
complex.h:22: warning: conflicting types for built-in function 'ctanh'
complex.h:23: warning: conflicting types for built-in function 'casinh'
complex.h:23: warning: conflicting types for built-in function 'cacosh'
complex.h:23: warning: conflicting types for built-in function 'catanh'
/home/feureau/Desktop/ccmath-2.2.1/geom
/home/feureau/Desktop/ccmath-2.2.1/intg
/home/feureau/Desktop/ccmath-2.2.1/matrix
In file included from chouse.c:9:
complex.h:18: warning: conflicting types for built-in function 'cabs'
complex.h:19: warning: conflicting types for built-in function 'csqrt'
complex.h:19: warning: conflicting types for built-in function 'cexp'
complex.h:19: warning: conflicting types for built-in function 'clog'
complex.h:20: warning: conflicting types for built-in function 'csin'
complex.h:20: warning: conflicting types for built-in function 'ccos'
complex.h:20: warning: conflicting types for built-in function 'ctan'
complex.h:21: warning: conflicting types for built-in function 'casin'
complex.h:21: warning: conflicting types for built-in function 'cacos'
complex.h:21: warning: conflicting types for built-in function 'catan'
complex.h:22: warning: conflicting types for built-in function 'csinh'
complex.h:22: warning: conflicting types for built-in function 'ccosh'
complex.h:22: warning: conflicting types for built-in function 'ctanh'
complex.h:23: warning: conflicting types for built-in function 'casinh'
complex.h:23: warning: conflicting types for built-in function 'cacosh'
complex.h:23: warning: conflicting types for built-in function 'catanh'
In file included from chousv.c:9:
complex.h:18: warning: conflicting types for built-in function 'cabs'
complex.h:19: warning: conflicting types for built-in function 'csqrt'
complex.h:19: warning: conflicting types for built-in function 'cexp'
complex.h:19: warning: conflicting types for built-in function 'clog'
complex.h:20: warning: conflicting types for built-in function 'csin'
complex.h:20: warning: conflicting types for built-in function 'ccos'
complex.h:20: warning: conflicting types for built-in function 'ctan'
complex.h:21: warning: conflicting types for built-in function 'casin'
complex.h:21: warning: conflicting types for built-in function 'cacos'
complex.h:21: warning: conflicting types for built-in function 'catan'
complex.h:22: warning: conflicting types for built-in function 'csinh'
complex.h:22: warning: conflicting types for built-in function 'ccosh'
complex.h:22: warning: conflicting types for built-in function 'ctanh'
complex.h:23: warning: conflicting types for built-in function 'casinh'
complex.h:23: warning: conflicting types for built-in function 'cacosh'
complex.h:23: warning: conflicting types for built-in function 'catanh'
In file included from cmattr.c:8:
complex.h:18: warning: conflicting types for built-in function 'cabs'
complex.h:19: warning: conflicting types for built-in function 'csqrt'
complex.h:19: warning: conflicting types for built-in function 'cexp'
complex.h:19: warning: conflicting types for built-in function 'clog'
complex.h:20: warning: conflicting types for built-in function 'csin'
complex.h:20: warning: conflicting types for built-in function 'ccos'
complex.h:20: warning: conflicting types for built-in function 'ctan'
complex.h:21: warning: conflicting types for built-in function 'casin'
complex.h:21: warning: conflicting types for built-in function 'cacos'
complex.h:21: warning: conflicting types for built-in function 'catan'
complex.h:22: warning: conflicting types for built-in function 'csinh'
complex.h:22: warning: conflicting types for built-in function 'ccosh'
complex.h:22: warning: conflicting types for built-in function 'ctanh'
complex.h:23: warning: conflicting types for built-in function 'casinh'
complex.h:23: warning: conflicting types for built-in function 'cacosh'
complex.h:23: warning: conflicting types for built-in function 'catanh'
In file included from cmcpy.c:8:
complex.h:18: warning: conflicting types for built-in function 'cabs'
complex.h:19: warning: conflicting types for built-in function 'csqrt'
complex.h:19: warning: conflicting types for built-in function 'cexp'
complex.h:19: warning: conflicting types for built-in function 'clog'
complex.h:20: warning: conflicting types for built-in function 'csin'
complex.h:20: warning: conflicting types for built-in function 'ccos'
complex.h:20: warning: conflicting types for built-in function 'ctan'
complex.h:21: warning: conflicting types for built-in function 'casin'
complex.h:21: warning: conflicting types for built-in function 'cacos'
complex.h:21: warning: conflicting types for built-in function 'catan'
complex.h:22: warning: conflicting types for built-in function 'csinh'
complex.h:22: warning: conflicting types for built-in function 'ccosh'
complex.h:22: warning: conflicting types for built-in function 'ctanh'
complex.h:23: warning: conflicting types for built-in function 'casinh'
complex.h:23: warning: conflicting types for built-in function 'cacosh'
complex.h:23: warning: conflicting types for built-in function 'catanh'
In file included from cminv.c:9:
complex.h:18: warning: conflicting types for built-in function 'cabs'
complex.h:19: warning: conflicting types for built-in function 'csqrt'
complex.h:19: warning: conflicting types for built-in function 'cexp'
complex.h:19: warning: conflicting types for built-in function 'clog'
complex.h:20: warning: conflicting types for built-in function 'csin'
complex.h:20: warning: conflicting types for built-in function 'ccos'
complex.h:20: warning: conflicting types for built-in function 'ctan'
complex.h:21: warning: conflicting types for built-in function 'casin'
complex.h:21: warning: conflicting types for built-in function 'cacos'
complex.h:21: warning: conflicting types for built-in function 'catan'
complex.h:22: warning: conflicting types for built-in function 'csinh'
complex.h:22: warning: conflicting types for built-in function 'ccosh'
complex.h:22: warning: conflicting types for built-in function 'ctanh'
complex.h:23: warning: conflicting types for built-in function 'casinh'
complex.h:23: warning: conflicting types for built-in function 'cacosh'
complex.h:23: warning: conflicting types for built-in function 'catanh'
In file included from cmmul.c:8:
complex.h:18: warning: conflicting types for built-in function 'cabs'
complex.h:19: warning: conflicting types for built-in function 'csqrt'
complex.h:19: warning: conflicting types for built-in function 'cexp'
complex.h:19: warning: conflicting types for built-in function 'clog'
complex.h:20: warning: conflicting types for built-in function 'csin'
complex.h:20: warning: conflicting types for built-in function 'ccos'
complex.h:20: warning: conflicting types for built-in function 'ctan'
complex.h:21: warning: conflicting types for built-in function 'casin'
complex.h:21: warning: conflicting types for built-in function 'cacos'
complex.h:21: warning: conflicting types for built-in function 'catan'
complex.h:22: warning: conflicting types for built-in function 'csinh'
complex.h:22: warning: conflicting types for built-in function 'ccosh'
complex.h:22: warning: conflicting types for built-in function 'ctanh'
complex.h:23: warning: conflicting types for built-in function 'casinh'
complex.h:23: warning: conflicting types for built-in function 'cacosh'
complex.h:23: warning: conflicting types for built-in function 'catanh'
In file included from cmmult.c:9:
complex.h:18: warning: conflicting types for built-in function 'cabs'
complex.h:19: warning: conflicting types for built-in function 'csqrt'
complex.h:19: warning: conflicting types for built-in function 'cexp'
complex.h:19: warning: conflicting types for built-in function 'clog'
complex.h:20: warning: conflicting types for built-in function 'csin'
complex.h:20: warning: conflicting types for built-in function 'ccos'
complex.h:20: warning: conflicting types for built-in function 'ctan'
complex.h:21: warning: conflicting types for built-in function 'casin'
complex.h:21: warning: conflicting types for built-in function 'cacos'
complex.h:21: warning: conflicting types for built-in function 'catan'
complex.h:22: warning: conflicting types for built-in function 'csinh'
complex.h:22: warning: conflicting types for built-in function 'ccosh'
complex.h:22: warning: conflicting types for built-in function 'ctanh'
complex.h:23: warning: conflicting types for built-in function 'casinh'
complex.h:23: warning: conflicting types for built-in function 'cacosh'
complex.h:23: warning: conflicting types for built-in function 'catanh'
In file included from cmprt.c:8:
complex.h:18: warning: conflicting types for built-in function 'cabs'
complex.h:19: warning: conflicting types for built-in function 'csqrt'
complex.h:19: warning: conflicting types for built-in function 'cexp'
complex.h:19: warning: conflicting types for built-in function 'clog'
complex.h:20: warning: conflicting types for built-in function 'csin'
complex.h:20: warning: conflicting types for built-in function 'ccos'
complex.h:20: warning: conflicting types for built-in function 'ctan'
complex.h:21: warning: conflicting types for built-in function 'casin'
complex.h:21: warning: conflicting types for built-in function 'cacos'
complex.h:21: warning: conflicting types for built-in function 'catan'
complex.h:22: warning: conflicting types for built-in function 'csinh'
complex.h:22: warning: conflicting types for built-in function 'ccosh'
complex.h:22: warning: conflicting types for built-in function 'ctanh'
complex.h:23: warning: conflicting types for built-in function 'casinh'
complex.h:23: warning: conflicting types for built-in function 'cacosh'
complex.h:23: warning: conflicting types for built-in function 'catanh'
cmprt.c: In function 'cmprt':
cmprt.c:12: warning: incompatible implicit declaration of built-in function 'printf'
In file included from csolv.c:9:
complex.h:18: warning: conflicting types for built-in function 'cabs'
complex.h:19: warning: conflicting types for built-in function 'csqrt'
complex.h:19: warning: conflicting types for built-in function 'cexp'
complex.h:19: warning: conflicting types for built-in function 'clog'
complex.h:20: warning: conflicting types for built-in function 'csin'
complex.h:20: warning: conflicting types for built-in function 'ccos'
complex.h:20: warning: conflicting types for built-in function 'ctan'
complex.h:21: warning: conflicting types for built-in function 'casin'
complex.h:21: warning: conflicting types for built-in function 'cacos'
complex.h:21: warning: conflicting types for built-in function 'catan'
complex.h:22: warning: conflicting types for built-in function 'csinh'
complex.h:22: warning: conflicting types for built-in function 'ccosh'
complex.h:22: warning: conflicting types for built-in function 'ctanh'
complex.h:23: warning: conflicting types for built-in function 'casinh'
complex.h:23: warning: conflicting types for built-in function 'cacosh'
complex.h:23: warning: conflicting types for built-in function 'catanh'
In file included from cvmul.c:8:
complex.h:18: warning: conflicting types for built-in function 'cabs'
complex.h:19: warning: conflicting types for built-in function 'csqrt'
complex.h:19: warning: conflicting types for built-in function 'cexp'
complex.h:19: warning: conflicting types for built-in function 'clog'
complex.h:20: warning: conflicting types for built-in function 'csin'
complex.h:20: warning: conflicting types for built-in function 'ccos'
complex.h:20: warning: conflicting types for built-in function 'ctan'
complex.h:21: warning: conflicting types for built-in function 'casin'
complex.h:21: warning: conflicting types for built-in function 'cacos'
complex.h:21: warning: conflicting types for built-in function 'catan'
complex.h:22: warning: conflicting types for built-in function 'csinh'
complex.h:22: warning: conflicting types for built-in function 'ccosh'
complex.h:22: warning: conflicting types for built-in function 'ctanh'
complex.h:23: warning: conflicting types for built-in function 'casinh'
complex.h:23: warning: conflicting types for built-in function 'cacosh'
complex.h:23: warning: conflicting types for built-in function 'catanh'
In file included from hconj.c:8:
complex.h:18: warning: conflicting types for built-in function 'cabs'
complex.h:19: warning: conflicting types for built-in function 'csqrt'
complex.h:19: warning: conflicting types for built-in function 'cexp'
complex.h:19: warning: conflicting types for built-in function 'clog'
complex.h:20: warning: conflicting types for built-in function 'csin'
complex.h:20: warning: conflicting types for built-in function 'ccos'
complex.h:20: warning: conflicting types for built-in function 'ctan'
complex.h:21: warning: conflicting types for built-in function 'casin'
complex.h:21: warning: conflicting types for built-in function 'cacos'
complex.h:21: warning: conflicting types for built-in function 'catan'
complex.h:22: warning: conflicting types for built-in function 'csinh'
complex.h:22: warning: conflicting types for built-in function 'ccosh'
complex.h:22: warning: conflicting types for built-in function 'ctanh'
complex.h:23: warning: conflicting types for built-in function 'casinh'
complex.h:23: warning: conflicting types for built-in function 'cacosh'
complex.h:23: warning: conflicting types for built-in function 'catanh'
In file included from heigval.c:9:
complex.h:18: warning: conflicting types for built-in function 'cabs'
complex.h:19: warning: conflicting types for built-in function 'csqrt'
complex.h:19: warning: conflicting types for built-in function 'cexp'
complex.h:19: warning: conflicting types for built-in function 'clog'
complex.h:20: warning: conflicting types for built-in function 'csin'
complex.h:20: warning: conflicting types for built-in function 'ccos'
complex.h:20: warning: conflicting types for built-in function 'ctan'
complex.h:21: warning: conflicting types for built-in function 'casin'
complex.h:21: warning: conflicting types for built-in function 'cacos'
complex.h:21: warning: conflicting types for built-in function 'catan'
complex.h:22: warning: conflicting types for built-in function 'csinh'
complex.h:22: warning: conflicting types for built-in function 'ccosh'
complex.h:22: warning: conflicting types for built-in function 'ctanh'
complex.h:23: warning: conflicting types for built-in function 'casinh'
complex.h:23: warning: conflicting types for built-in function 'cacosh'
complex.h:23: warning: conflicting types for built-in function 'catanh'
In file included from heigvec.c:9:
complex.h:18: warning: conflicting types for built-in function 'cabs'
complex.h:19: warning: conflicting types for built-in function 'csqrt'
complex.h:19: warning: conflicting types for built-in function 'cexp'
complex.h:19: warning: conflicting types for built-in function 'clog'
complex.h:20: warning: conflicting types for built-in function 'csin'
complex.h:20: warning: conflicting types for built-in function 'ccos'
complex.h:20: warning: conflicting types for built-in function 'ctan'
complex.h:21: warning: conflicting types for built-in function 'casin'
complex.h:21: warning: conflicting types for built-in function 'cacos'
complex.h:21: warning: conflicting types for built-in function 'catan'
complex.h:22: warning: conflicting types for built-in function 'csinh'
complex.h:22: warning: conflicting types for built-in function 'ccosh'
complex.h:22: warning: conflicting types for built-in function 'ctanh'
complex.h:23: warning: conflicting types for built-in function 'casinh'
complex.h:23: warning: conflicting types for built-in function 'cacosh'
complex.h:23: warning: conflicting types for built-in function 'catanh'
In file included from hevmax.c:9:
complex.h:18: warning: conflicting types for built-in function 'cabs'
complex.h:19: warning: conflicting types for built-in function 'csqrt'
complex.h:19: warning: conflicting types for built-in function 'cexp'
complex.h:19: warning: conflicting types for built-in function 'clog'
complex.h:20: warning: conflicting types for built-in function 'csin'
complex.h:20: warning: conflicting types for built-in function 'ccos'
complex.h:20: warning: conflicting types for built-in function 'ctan'
complex.h:21: warning: conflicting types for built-in function 'casin'
complex.h:21: warning: conflicting types for built-in function 'cacos'
complex.h:21: warning: conflicting types for built-in function 'catan'
complex.h:22: warning: conflicting types for built-in function 'csinh'
complex.h:22: warning: conflicting types for built-in function 'ccosh'
complex.h:22: warning: conflicting types for built-in function 'ctanh'
complex.h:23: warning: conflicting types for built-in function 'casinh'
complex.h:23: warning: conflicting types for built-in function 'cacosh'
complex.h:23: warning: conflicting types for built-in function 'catanh'
In file included from hmgen.c:9:
complex.h:18: warning: conflicting types for built-in function 'cabs'
complex.h:19: warning: conflicting types for built-in function 'csqrt'
complex.h:19: warning: conflicting types for built-in function 'cexp'
complex.h:19: warning: conflicting types for built-in function 'clog'
complex.h:20: warning: conflicting types for built-in function 'csin'
complex.h:20: warning: conflicting types for built-in function 'ccos'
complex.h:20: warning: conflicting types for built-in function 'ctan'
complex.h:21: warning: conflicting types for built-in function 'casin'
complex.h:21: warning: conflicting types for built-in function 'cacos'
complex.h:21: warning: conflicting types for built-in function 'catan'
complex.h:22: warning: conflicting types for built-in function 'csinh'
complex.h:22: warning: conflicting types for built-in function 'ccosh'
complex.h:22: warning: conflicting types for built-in function 'ctanh'
complex.h:23: warning: conflicting types for built-in function 'casinh'
complex.h:23: warning: conflicting types for built-in function 'cacosh'
complex.h:23: warning: conflicting types for built-in function 'catanh'
In file included from qrecvc.c:8:
complex.h:18: warning: conflicting types for built-in function 'cabs'
complex.h:19: warning: conflicting types for built-in function 'csqrt'
complex.h:19: warning: conflicting types for built-in function 'cexp'
complex.h:19: warning: conflicting types for built-in function 'clog'
complex.h:20: warning: conflicting types for built-in function 'csin'
complex.h:20: warning: conflicting types for built-in function 'ccos'
complex.h:20: warning: conflicting types for built-in function 'ctan'
complex.h:21: warning: conflicting types for built-in function 'casin'
complex.h:21: warning: conflicting types for built-in function 'cacos'
complex.h:21: warning: conflicting types for built-in function 'catan'
complex.h:22: warning: conflicting types for built-in function 'csinh'
complex.h:22: warning: conflicting types for built-in function 'ccosh'
complex.h:22: warning: conflicting types for built-in function 'ctanh'
complex.h:23: warning: conflicting types for built-in function 'casinh'
complex.h:23: warning: conflicting types for built-in function 'cacosh'
complex.h:23: warning: conflicting types for built-in function 'catanh'
In file included from trncm.c:8:
complex.h:18: warning: conflicting types for built-in function 'cabs'
complex.h:19: warning: conflicting types for built-in function 'csqrt'
complex.h:19: warning: conflicting types for built-in function 'cexp'
complex.h:19: warning: conflicting types for built-in function 'clog'
complex.h:20: warning: conflicting types for built-in function 'csin'
complex.h:20: warning: conflicting types for built-in function 'ccos'
complex.h:20: warning: conflicting types for built-in function 'ctan'
complex.h:21: warning: conflicting types for built-in function 'casin'
complex.h:21: warning: conflicting types for built-in function 'cacos'
complex.h:21: warning: conflicting types for built-in function 'catan'
complex.h:22: warning: conflicting types for built-in function 'csinh'
complex.h:22: warning: conflicting types for built-in function 'ccosh'
complex.h:22: warning: conflicting types for built-in function 'ctanh'
complex.h:23: warning: conflicting types for built-in function 'casinh'
complex.h:23: warning: conflicting types for built-in function 'cacosh'
complex.h:23: warning: conflicting types for built-in function 'catanh'
In file included from unitary.c:9:
complex.h:18: warning: conflicting types for built-in function 'cabs'
complex.h:19: warning: conflicting types for built-in function 'csqrt'
complex.h:19: warning: conflicting types for built-in function 'cexp'
complex.h:19: warning: conflicting types for built-in function 'clog'
complex.h:20: warning: conflicting types for built-in function 'csin'
complex.h:20: warning: conflicting types for built-in function 'ccos'
complex.h:20: warning: conflicting types for built-in function 'ctan'
complex.h:21: warning: conflicting types for built-in function 'casin'
complex.h:21: warning: conflicting types for built-in function 'cacos'
complex.h:21: warning: conflicting types for built-in function 'catan'
complex.h:22: warning: conflicting types for built-in function 'csinh'
complex.h:22: warning: conflicting types for built-in function 'ccosh'
complex.h:22: warning: conflicting types for built-in function 'ctanh'
complex.h:23: warning: conflicting types for built-in function 'casinh'
complex.h:23: warning: conflicting types for built-in function 'cacosh'
complex.h:23: warning: conflicting types for built-in function 'catanh'
In file included from utrncm.c:9:
complex.h:18: warning: conflicting types for built-in function 'cabs'
complex.h:19: warning: conflicting types for built-in function 'csqrt'
complex.h:19: warning: conflicting types for built-in function 'cexp'
complex.h:19: warning: conflicting types for built-in function 'clog'
complex.h:20: warning: conflicting types for built-in function 'csin'
complex.h:20: warning: conflicting types for built-in function 'ccos'
complex.h:20: warning: conflicting types for built-in function 'ctan'
complex.h:21: warning: conflicting types for built-in function 'casin'
complex.h:21: warning: conflicting types for built-in function 'cacos'
complex.h:21: warning: conflicting types for built-in function 'catan'
complex.h:22: warning: conflicting types for built-in function 'csinh'
complex.h:22: warning: conflicting types for built-in function 'ccosh'
complex.h:22: warning: conflicting types for built-in function 'ctanh'
complex.h:23: warning: conflicting types for built-in function 'casinh'
complex.h:23: warning: conflicting types for built-in function 'cacosh'
complex.h:23: warning: conflicting types for built-in function 'catanh'
In file included from utrnhm.c:9:
complex.h:18: warning: conflicting types for built-in function 'cabs'
complex.h:19: warning: conflicting types for built-in function 'csqrt'
complex.h:19: warning: conflicting types for built-in function 'cexp'
complex.h:19: warning: conflicting types for built-in function 'clog'
complex.h:20: warning: conflicting types for built-in function 'csin'
complex.h:20: warning: conflicting types for built-in function 'ccos'
complex.h:20: warning: conflicting types for built-in function 'ctan'
complex.h:21: warning: conflicting types for built-in function 'casin'
complex.h:21: warning: conflicting types for built-in function 'cacos'
complex.h:21: warning: conflicting types for built-in function 'catan'
complex.h:22: warning: conflicting types for built-in function 'csinh'
complex.h:22: warning: conflicting types for built-in function 'ccosh'
complex.h:22: warning: conflicting types for built-in function 'ctanh'
complex.h:23: warning: conflicting types for built-in function 'casinh'
complex.h:23: warning: conflicting types for built-in function 'cacosh'
complex.h:23: warning: conflicting types for built-in function 'catanh'
/home/feureau/Desktop/ccmath-2.2.1/roots
In file included from plrt.c:9:
complex.h:18: warning: conflicting types for built-in function 'cabs'
complex.h:19: warning: conflicting types for built-in function 'csqrt'
complex.h:19: warning: conflicting types for built-in function 'cexp'
complex.h:19: warning: conflicting types for built-in function 'clog'
complex.h:20: warning: conflicting types for built-in function 'csin'
complex.h:20: warning: conflicting types for built-in function 'ccos'
complex.h:20: warning: conflicting types for built-in function 'ctan'
complex.h:21: warning: conflicting types for built-in function 'casin'
complex.h:21: warning: conflicting types for built-in function 'cacos'
complex.h:21: warning: conflicting types for built-in function 'catan'
complex.h:22: warning: conflicting types for built-in function 'csinh'
complex.h:22: warning: conflicting types for built-in function 'ccosh'
complex.h:22: warning: conflicting types for built-in function 'ctanh'
complex.h:23: warning: conflicting types for built-in function 'casinh'
complex.h:23: warning: conflicting types for built-in function 'cacosh'
complex.h:23: warning: conflicting types for built-in function 'catanh'
In file included from polyc.c:8:
complex.h:18: warning: conflicting types for built-in function 'cabs'
complex.h:19: warning: conflicting types for built-in function 'csqrt'
complex.h:19: warning: conflicting types for built-in function 'cexp'
complex.h:19: warning: conflicting types for built-in function 'clog'
complex.h:20: warning: conflicting types for built-in function 'csin'
complex.h:20: warning: conflicting types for built-in function 'ccos'
complex.h:20: warning: conflicting types for built-in function 'ctan'
complex.h:21: warning: conflicting types for built-in function 'casin'
complex.h:21: warning: conflicting types for built-in function 'cacos'
complex.h:21: warning: conflicting types for built-in function 'catan'
complex.h:22: warning: conflicting types for built-in function 'csinh'
complex.h:22: warning: conflicting types for built-in function 'ccosh'
complex.h:22: warning: conflicting types for built-in function 'ctanh'
complex.h:23: warning: conflicting types for built-in function 'casinh'
complex.h:23: warning: conflicting types for built-in function 'cacosh'
complex.h:23: warning: conflicting types for built-in function 'catanh'
/home/feureau/Desktop/ccmath-2.2.1/sfunc
/home/feureau/Desktop/ccmath-2.2.1/simu
/home/feureau/Desktop/ccmath-2.2.1/sort
/home/feureau/Desktop/ccmath-2.2.1/statf
/home/feureau/Desktop/ccmath-2.2.1/tseries
In file included from sany.c:8:
../ccmath.h:707: warning: conflicting types for built-in function 'cabs'
../ccmath.h:711: warning: conflicting types for built-in function 'cexp'
../ccmath.h:713: warning: conflicting types for built-in function 'clog'
../ccmath.h:715: warning: conflicting types for built-in function 'csinh'
../ccmath.h:717: warning: conflicting types for built-in function 'ccosh'
../ccmath.h:719: warning: conflicting types for built-in function 'ctanh'
../ccmath.h:721: warning: conflicting types for built-in function 'casinh'
../ccmath.h:723: warning: conflicting types for built-in function 'cacosh'
../ccmath.h:725: warning: conflicting types for built-in function 'catanh'
../ccmath.h:727: warning: conflicting types for built-in function 'casin'
../ccmath.h:729: warning: conflicting types for built-in function 'cacos'
../ccmath.h:731: warning: conflicting types for built-in function 'catan'
../ccmath.h:733: warning: conflicting types for built-in function 'csqrt'
../ccmath.h:735: warning: conflicting types for built-in function 'csin'
../ccmath.h:737: warning: conflicting types for built-in function 'ccos'
../ccmath.h:739: warning: conflicting types for built-in function 'ctan'
/home/feureau/Desktop/ccmath-2.2.1/util
bpat.c: In function 'bitpc':
bpat.c:13: warning: incompatible implicit declaration of built-in function 'printf'
bpat.c:14: warning: incompatible implicit declaration of built-in function 'printf'
bpat.c: In function 'bitps':
bpat.c:21: warning: incompatible implicit declaration of built-in function 'printf'
bpat.c:22: warning: incompatible implicit declaration of built-in function 'printf'
bpat.c: In function 'bitpl':
bpat.c:29: warning: incompatible implicit declaration of built-in function 'printf'
bpat.c:30: warning: incompatible implicit declaration of built-in function 'printf'
bpat.c: In function 'bitpf':
bpat.c:39: warning: incompatible implicit declaration of built-in function 'printf'
bpat.c:43: warning: incompatible implicit declaration of built-in function 'printf'
bpat.c: In function 'bitpd':
bpat.c:52: warning: incompatible implicit declaration of built-in function 'printf'
bpat.c:56: warning: incompatible implicit declaration of built-in function 'printf'
bpatx.c: In function 'bpatx':
bpatx.c:13: warning: incompatible implicit declaration of built-in function 'printf'
bpatx.c:19: warning: incompatible implicit declaration of built-in function 'printf'
/home/feureau/Desktop/ccmath-2.2.1/xarm
xlog.c: In function 'xlog':
xlog.c:12: warning: incompatible implicit declaration of built-in function 'printf'
xsqrt.c: In function 'xsqrt':
xsqrt.c:12: warning: incompatible implicit declaration of built-in function 'printf'
xtrig.c:9: warning: conflicting types for built-in function 'ctan'
solv.s: Assembler messages:
solv.s:13: Error: suffix or operands invalid for `push'
solv.s:16: Error: suffix or operands invalid for `push'
solv.s:17: Error: suffix or operands invalid for `push'
solv.s:18: Error: suffix or operands invalid for `push'
solv.s:20: Error: suffix or operands invalid for `push'
solv.s:22: Error: suffix or operands invalid for `push'
solv.s:199: Error: suffix or operands invalid for `push'
solv.s:374: Error: suffix or operands invalid for `push'
solv.s:379: Error: suffix or operands invalid for `pop'
solv.s:380: Error: suffix or operands invalid for `pop'
solv.s:381: Error: suffix or operands invalid for `pop'
solv.s:383: Error: suffix or operands invalid for `pop'
mv: cannot stat `*.o': No such file or directory
ar: creating libccm.a
ld: airy.o: relocation R_X86_64_32 against `a local symbol' can not be used when making a shared object; recompile with -fPIC
airy.o: could not read symbols: Bad value
feureau@Coconut8:~/Desktop/ccmath-2.2.1$ 


I tried it first with the "script" you gave me and then manually line by line in a different folder but it seems to spit out the same result.
Thanks a bunch with sugar lumps on top. :D

---

### Post by geirha on 2007-11-16
A little googling suggests it's a problem of 64bit vs 32bit, yes. I'm not sure how to get past it really, I haven't messed much with assembler, and I don't have a 64bit architecture. I'm guessing that changing the last part of **makelibs.sh** might work (changes marked with green):
```
if [ $F = "y" ]
  then cd $MDR/matrix
    cc [COLOR="Green"]--32[/COLOR] -c -O3 solv.s
    mv *.o $LSOD
    cd $MDR/simu
    cc [COLOR="Green"]--32[/COLOR] -c -O3 *.s
    mv *.o $LSOD
fi
cd $LSOD
ar r libccm.a *.o
[COLOR="Green"]gcc -m32[/COLOR] -shared -o libccm.so *.o
rm *.o
```
(based on this thread [http://osdir.com/ml/linux.assembly/2006-12/msg00006.html](http://osdir.com/ml/linux.assembly/2006-12/msg00006.html))

Alternatively, there seems to be regular C-code that does the same job (except it's less optimized I'm guessing), which you can use by running the non_intel.sh script first, and specify no when it asks if you have big-endian. Then when you run the makelibs script, specify no when it asks if you have intel arch.

---

### Post by Feureau on 2007-11-18
Hi, geirha
Thanks for the instructions, but I just can't get this thing working. So, I'm giving up.
Thanks for everything. You're what we need more in this community. :)

---

