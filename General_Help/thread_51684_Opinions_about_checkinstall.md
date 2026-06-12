---
title: "Opinions about checkinstall"
date: 2005-07-24
forum: General Help
---

### Post by easy_target on 2005-07-24
Hi all,

I am currently in the process of becoming an initiate in linux packaging and compiling, but there are currently out there several ways of compiling, creating and managing packages. In one of my errandss through google I stumbled across checkinstall. I would like to know your opinions about it and if you would recommend it or suggest a better way of performing these tasks. For now I am only limiting myself to "home" packages (they won't go in any repo server or anything) but feel free to consider sharing your views with us!

---

### Post by bored2k on 2005-07-24
Well, I've had nothing but love coming from checkinstall. It's basically the only thing I use for compiling my packages (just like easy_target's, for my own use). It's by far the easiest method I have encountered for making debian packages and it's easy to setup. This morning I used it to successfully create packages for xmms/bmp scrobbler and bmp-docklet plugins wich can be found [here](http://bored2k.cjb.net/) .

If anyone knows something better and at least _half_ as easy as checkinstall, I would also love to know about it.

---

### Post by Xian on 2005-07-24
Have you gotten it to successfuly install a gdesklets compile?
That's never worked on my box.

And I just tried it with Kbootsplash but no dice there either.

---

### Post by bored2k on 2005-07-24
[QUOTE=Xian]Have you gotten it to successfuly install a gdesklets compile?
That's never worked on my box.

And I just tried it with Kbootsplash but no dice there either.[/QUOTE]
 It's been a while since I've touched any desklets,  so in that case I wouldn't know. But, if you manage to compile that package normally with make install, why wouldn't it work with checkinstall?

---

### Post by Xian on 2005-07-24
[QUOTE=bored2k]It's been a while since I've touched any desklets,  so in that case I wouldn't know. But, if you manage to compile that package normally with make install, why wouldn't it work with checkinstall?[/QUOTE]
Beats me, that's why I asked. Maybe the python causes problems???

---

### Post by Xian on 2005-07-25
Anyway, here's some reasons not to use checkinstall as posted in a [thread](http://forums.suselinuxsupport.de/index.php?showtopic=4343&pid=27209&mode=threaded&show=&st=?entry27209) at suseforums by [Guru](http://linux01.gwdg.de/~pbleser/index.php).

[i]"I think I'm in a good position to comment on this  , so here are my .02EUR:

The quality of RPMs made with checkinstall is very, very poor. It's really more of a "quick hack" than a good way of building stable RPM packages. I never used checkinstall (besides some testing) and never will.

The good way of making RPMs is by writing .spec files, building (with rpmbuild), and testing them. It also requires a little experience to know how your distribution (SuSE Linux, in this case) usually organizes files, how and where (e.g. GNOME stuff in /opt/gnome, KDE stuff in /opt/kde3, PAM configuration files in /etc/pam.d, ...) because they differ on the various RPM-based distributions and sources usually only provide proper defaults for Redhat, if at all. One also has to provide good integration with the system: init scripts for daemons/services, using proper file locations and directories, ...That's something checkinstall won't do.

As an example: RPM packages should never install files into /usr/local.
That's for stuff you build from sources, only. It's the whole point of having /usr and /usr/local If you use checkinstall and don't provide proper flags to ./configure, it won't be integrated properly into the distribution.

Believe me, quality is very important, as having badly organized/integrated packages only proves to be more troublesome than anything else; take usr-local-bin.org's glib/gtk 2.4 packages: they break almost everything unless you really, really know what you are doing and how to handle the issues.

I've been using every version of SuSE Linux since 5.0 and providing packages for the community since 7.2 - believe me, it's not that trivial.

As the whole idea behind RPM packages is to provide an easy way for users to install software without the hassle of building from sources, having to sort out binary dependencies, etc..., one should really care about quality when releasing RPMs into the (free) world"[/i]

---

### Post by doclivingston on 2005-07-25
CheckInstall is great for when you compile software by yourself, so that you can uninstall it easily. It doesn't work that well for creating packages that you can distribute to others - for a start it doesn't include any dependency information.

---

### Post by cutOff on 2005-07-25
[http://women.alioth.debian.org/wiki/index.php/English/PackagingTutorial](http://women.alioth.debian.org/wiki/index.php/English/PackagingTutorial) 

I did not try it though.

---

### Post by bored2k on 2005-07-25
[QUOTE=cutOff][http://women.alioth.debian.org/wiki/index.php/English/PackagingTutorial](http://women.alioth.debian.org/wiki/index.php/English/PackagingTutorial) 

I did not try it though.[/QUOTE]
 This guide! Thanks a lot for it :D.

---

### Post by easy_target on 2005-07-25
[QUOTE=doclivingston]CheckInstall is great for when you compile software by yourself, so that you can uninstall it easily. It doesn't work that well for creating packages that you can distribute to others - for a start it doesn't include any dependency information.[/QUOTE]

I agree with doclivingston. The advantage of using checkinstall over the regular make, make- install is that you can keep track of the package you created yourself (even if it is not perfect or up to the norms) and very easily removable in case you find a better or updated version of a package on the internet  :).

By the way, the tutorial is excellent! I will try dh_make in a few unconspicuous packages and see how it works. But I am still very attracted by checkinstall's ease of use and straightforwardness.

---

### Post by cutOff on 2005-07-25
[QUOTE=cutOff][http://women.alioth.debian.org/wiki/index.php/English/PackagingTutorial](http://women.alioth.debian.org/wiki/index.php/English/PackagingTutorial) 

I did not try it though.[/QUOTE]
I've just tried this method and I've got some errors when compiling

```
/usr/bin/make
make[1]: Entering directory `/home/cutoff/debian/wmforkplop-0.9.2'
/usr/bin/make  all-am
make[2]: Entering directory `/home/cutoff/debian/wmforkplop-0.9.2'
if i386-linux-gcc -DHAVE_CONFIG_H -DPKGDATADIR="\"/usr/share/wmforkplop\"" -I. -I. -I.     -I/usr/include/libgtop-2.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -O3 -fomit-frame-pointer -ffast-math -Wall -W  -I/usr/X11R6/include -MT wmforkplop-wmforkplop.o -MD -MP -MF ".deps/wmforkplop-wmforkplop.Tpo" \
  -c -o wmforkplop-wmforkplop.o `test -f 'wmforkplop.c' || echo './'`wmforkplop.c; \
then mv -f ".deps/wmforkplop-wmforkplop.Tpo" ".deps/wmforkplop-wmforkplop.Po"; \
else rm -f ".deps/wmforkplop-wmforkplop.Tpo"; exit 1; \
fi
En el fichero incluído de wmforkplop.h:9,
                 de wmforkplop.c:35:
procstat.h:5:26: glibtop/open.h: No existe el fichero o el directorio
En el fichero incluído de procstat.h:8,
                 de wmforkplop.h:9,
                 de wmforkplop.c:35:
/usr/include/libgtop-2.0/glibtop/parameter.h:26:26: glibtop/open.h: No existe el fichero o el directorio
make[2]: *** [wmforkplop-wmforkplop.o] Error 1
make[2]: Leaving directory `/home/cutoff/debian/wmforkplop-0.9.2'
make[1]: *** [all] Error 2
make[1]: Leaving directory `/home/cutoff/debian/wmforkplop-0.9.2'
make: *** [build-stamp] Error 2
debuild: fatal error at line 764:
dpkg-buildpackage failed!
```
Does someone know what can happen?

---

### Post by cutOff on 2005-07-26
*bump*

---

