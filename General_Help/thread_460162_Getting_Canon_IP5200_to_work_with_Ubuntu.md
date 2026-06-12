---
title: "Getting Canon IP5200 to work with Ubuntu"
date: 2007-05-31
forum: General Help
---

### Post by oldnat on 2007-05-31
I am also still trying to find a possibility to get my Canon iP5200 work.
No alternative, sell it and buy another supported one, easily because the supported ones are by far not so good that this darn Canon beast. So I stuck to it. Back to Windows? No way - paying 400 $ vor a vista which does not run any of my xp software? instead of 30 $ for a turboprint... am not mad.

But am confident that the Community who has more competence than me shall come up with a solution which I can use then.

I was using Windows ever since it derived from Borland Framework (yes, MS did NOT invent the wheel just marketinged it) and with that vista thing I got absolutely fed up.

Ubuntu gave me just what I wanted to have. A system which just works.

Even if some pieces of thirdparty ignorants still does not work. It shall.

So ubuntu.

Regards,

Nathalie

---

### Post by aysiu on 2007-05-31
Maybe [this](https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/CanonPrinters/CanonPixmaIP4200#preview) might help.

By the way, I've moved your post to its own thread, so it can get the proper support it deserves.

---

### Post by oldnat on 2007-06-17
Alas, it does not.
It say explicitly, that this does not work for amd64.
I received support from somebody in German (ashame, I do not know any more who) who suggested to do a 

sudo dpkg --force-architecture -i *.deb

and if that does not work to do  a

apt-get install ia32-libs ia32-libs-gtk ia32-libs-sdl

but the problem is that already the alien throws up in the alien.

The first error is:

dpkg-shlibdeps: warning: unable to find dependency information for shared library libpopt (soname 0, path libpopt.so.0, dependency field Depends)
dpkg-shlibdeps: warning: could not find any packages for libcups.so.2

...and it ends with:

[B]dh_gencontrol
dpkg-gencontrol: error: current build architecture amd64 does not appear in package's list (i386)
dh_gencontrol: command returned error code 65280
make: *** [binary-arch] Error 1

Package build failed. Here's the log:

...
dpkg-gencontrol: error: current build architecture amd64 does not appear in package's list (i386)
dh_gencontrol: command returned error code 65280
make: *** [binary-arch] Error 1
        find cnijfilter-common-2.60 -type d -exec chmod 755 {} ;
find: cnijfilter-common-2.60: No such file or directory
        rm -rf cnijfilter-common-2.60

But the dir is there!:

nathalie@miriam:~/canon$ ls
cnijfilter-common-2.60             cnijfilter-common-2.60-1.src.rpm   cnijfilter-ip4200-lprng-2.60-1.i386.rpm
cnijfilter-common-2.60-1.i386.rpm  cnijfilter-ip4200-2.60-1.i386.rpm  iP4200_Linux_260.tar.gz
nathalie@miriam:~/canon$ 

But no *deb files anywhere inside...


So please, where to go on now?

Thank you

Nathalie

[full veryverbose output attached as a file]

---

### Post by Golyadkin on 2007-06-17
This is very strange because my Canon iP 4200 PIXMA works straight out of the box with Ubuntu 64 bit, I never had to install anything whatsoever.

---

