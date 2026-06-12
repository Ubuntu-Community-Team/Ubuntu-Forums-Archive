---
title: "how do I install an RPM file without that alien crap?"
date: 2012-10-16
forum: General Help
---

### Post by kcirrab on 2012-10-16
I just want to know how to install an .rpm files WITHOUT converting them... alien doesn't work half the time and I don't want to screw with trouble shooting as I don't like the method anyway...

I seam to remember back in the day it was a simple terminal command... 

Sorry to be kinda demanding, I just hate that after all of these years linux still can't get a standardized installer... although Debian is trying..

Thanks!

---

### Post by GolanTrevize on 2012-10-16
Ubuntu is based on Debian and uses the Debian Package Manager. Therefore it is necessary to transform rpm to deb Packages.

If you prefer RPM than you should use a rpm based distribution (e.g. RedHat)

Btw.: It sounds as if you would have the need to install lots of RPM-Files, not just one or two. - The Ubuntu repositories are quite huge and contain almost anything one could demand. I did not have to install a rpm for years - and i am min 8h/day on ubuntu-computers ...

So might it be, that you could need help, searching the ubuntu-repositories?

greets
golan

---

### Post by Lars Noodén on 2012-10-16
RPMs are not for Ubuntu.  What packages are you trying to find?  Chances are it's already in the repository.  If not, you could try Debian's repositories.

---

### Post by kurt18947 on 2012-10-16
> **GolanTrevize said:**
> Ubuntu is based on Debian and uses the Debian Package Manager. Therefore it is necessary to transform rpm to deb Packages.

**If you prefer RPM than you should use a rpm based distribution** (e.g. RedHat)

Btw.: It sounds as if you would have the need to install lots of RPM-Files, not just one or two. - The Ubuntu repositories are quite huge and contain almost anything one could demand. I did not have to install a rpm for years - and i am min 8h/day on ubuntu-computers ...

So might it be, that you could need help, searching the ubuntu-repositories?

greets
golan

That is an option.  PCLinuxOS uses .rpm but also uses apt-get, sort of a hybrid package management system it seems.  OpenSUSE also uses .rpm.

---

### Post by kcirrab on 2012-10-16
maybe I could just get some help getting alien to work.. as I favor Ubuntu over other distro's... sorry for getting off on the wrong foot...

I was wanting to install java directly from java's website not the "icedtea" java.. but alien will not convert it.... here is the print out from terminal..



```
allexander@ubuntu:~$ sudo alien '/home/allexander/Downloads/jre-7u7-linux-x64.rpm' 
[sudo] password for allexander: 
Warning: Skipping conversion of scripts in package jre: postinst postrm prerm
Warning: Use the --scripts parameter to include the scripts.
Package build failed. Here's the log:
dh_testdir
dh_testdir
dh_testroot
dh_prep
dh_installdirs
dh_installdocs
dh_installchangelogs
find . -maxdepth 1 -mindepth 1 -not -name debian -print0 | \
		xargs -0 -r -i cp -a {} debian/jre
dh_compress
dh_makeshlibs
dh_installdeb
dh_shlibdeps
dpkg-shlibdeps: warning: Can't extract name and version from library name `libjli.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libjli.so'
dpkg-shlibdeps: warning: couldn't find library libjvm.so needed by debian/jre/usr/java/jre1.7.0_07/lib/amd64/libt2k.so (ELF format: 'elf64-x86-64'; RPATH: '/usr/java/jre1.7.0_07/lib/amd64').
dpkg-shlibdeps: warning: Can't extract name and version from library name `libjava.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libjava.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libfontmanager.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libfontmanager.so'
dpkg-shlibdeps: warning: couldn't find library libjvm.so needed by debian/jre/usr/java/jre1.7.0_07/lib/amd64/libzip.so (ELF format: 'elf64-x86-64'; RPATH: '/usr/java/jre1.7.0_07/lib/amd64').
dpkg-shlibdeps: warning: Can't extract name and version from library name `libjava.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libjava.so'
dpkg-shlibdeps: warning: couldn't find library libjvm.so needed by debian/jre/usr/java/jre1.7.0_07/lib/amd64/libsunec.so (ELF format: 'elf64-x86-64'; RPATH: '').
dpkg-shlibdeps: warning: couldn't find library libjava.so needed by debian/jre/usr/java/jre1.7.0_07/lib/amd64/libsunec.so (ELF format: 'elf64-x86-64'; RPATH: '').
dpkg-shlibdeps: warning: couldn't find library libjvm.so needed by debian/jre/usr/java/jre1.7.0_07/lib/amd64/librmi.so (ELF format: 'elf64-x86-64'; RPATH: '/usr/java/jre1.7.0_07/lib/amd64').
dpkg-shlibdeps: warning: Can't extract name and version from library name `libjava.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libjava.so'
dpkg-shlibdeps: warning: couldn't find library libjvm.so needed by debian/jre/usr/java/jre1.7.0_07/lib/amd64/libjsound.so (ELF format: 'elf64-x86-64'; RPATH: '/usr/java/jre1.7.0_07/lib/amd64').
dpkg-shlibdeps: warning: Can't extract name and version from library name `libjava.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libjava.so'
dpkg-shlibdeps: warning: couldn't find library libjvm.so needed by debian/jre/usr/java/jre1.7.0_07/lib/amd64/libkcms.so (ELF format: 'elf64-x86-64'; RPATH: '/usr/java/jre1.7.0_07/lib/amd64').
dpkg-shlibdeps: warning: Can't extract name and version from library name `libjava.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libjava.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libnet.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libnet.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libjava.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libjava.so'
dpkg-shlibdeps: warning: couldn't find library libjvm.so needed by debian/jre/usr/java/jre1.7.0_07/lib/amd64/headless/libmawt.so (ELF format: 'elf64-x86-64'; RPATH: '/usr/java/jre1.7.0_07/lib/amd64/headless:/usr/java/jre1.7.0_07/lib/amd64/headless/..').
dpkg-shlibdeps: warning: Can't extract name and version from library name `libawt.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libawt.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libjava.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libjava.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libjli.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libjli.so'
dpkg-shlibdeps: warning: couldn't find library libjvm.so needed by debian/jre/usr/java/jre1.7.0_07/lib/amd64/libjaas_unix.so (ELF format: 'elf64-x86-64'; RPATH: '/usr/java/jre1.7.0_07/lib/amd64').
dpkg-shlibdeps: warning: Can't extract name and version from library name `libjava.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libjava.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libjli.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libjli.so'
dpkg-shlibdeps: warning: couldn't find library libjvm.so needed by debian/jre/usr/java/jre1.7.0_07/lib/amd64/libj2pcsc.so (ELF format: 'elf64-x86-64'; RPATH: '/usr/java/jre1.7.0_07/lib/amd64').
dpkg-shlibdeps: warning: Can't extract name and version from library name `libjava.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libjava.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libjli.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libjli.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libjli.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libjli.so'
dpkg-shlibdeps: warning: couldn't find library libjvm.so needed by debian/jre/usr/java/jre1.7.0_07/lib/amd64/libjpeg.so (ELF format: 'elf64-x86-64'; RPATH: '/usr/java/jre1.7.0_07/lib/amd64').
dpkg-shlibdeps: warning: Can't extract name and version from library name `libjava.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libjava.so'
dpkg-shlibdeps: warning: couldn't find library libjvm.so needed by debian/jre/usr/java/jre1.7.0_07/lib/amd64/libdcpr.so (ELF format: 'elf64-x86-64'; RPATH: '/usr/java/jre1.7.0_07/lib/amd64').
dpkg-shlibdeps: warning: Can't extract name and version from library name `libjava.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libjava.so'
dpkg-shlibdeps: warning: couldn't find library libjvm.so needed by debian/jre/usr/java/jre1.7.0_07/lib/amd64/libj2pkcs11.so (ELF format: 'elf64-x86-64'; RPATH: '/usr/java/jre1.7.0_07/lib/amd64').
dpkg-shlibdeps: warning: Can't extract name and version from library name `libjava.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libjava.so'
dpkg-shlibdeps: warning: couldn't find library libjvm.so needed by debian/jre/usr/java/jre1.7.0_07/lib/amd64/libjava.so (ELF format: 'elf64-x86-64'; RPATH: '/usr/java/jre1.7.0_07/lib/amd64').
dpkg-shlibdeps: warning: Can't extract name and version from library name `libverify.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libverify.so'
dpkg-shlibdeps: warning: couldn't find library libjvm.so needed by debian/jre/usr/java/jre1.7.0_07/lib/amd64/libverify.so (ELF format: 'elf64-x86-64'; RPATH: '/usr/java/jre1.7.0_07/lib/amd64').
dpkg-shlibdeps: warning: Can't extract name and version from library name `libjli.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libjli.so'
dpkg-shlibdeps: warning: couldn't find library libgstreamer-lite.so needed by debian/jre/usr/java/jre1.7.0_07/lib/amd64/libgstplugins-lite.so (ELF format: 'elf64-x86-64'; RPATH: '').
dpkg-shlibdeps: warning: couldn't find library libjvm.so needed by debian/jre/usr/java/jre1.7.0_07/lib/amd64/libmanagement.so (ELF format: 'elf64-x86-64'; RPATH: '/usr/java/jre1.7.0_07/lib/amd64').
dpkg-shlibdeps: warning: Can't extract name and version from library name `libjava.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libjava.so'
dpkg-shlibdeps: warning: couldn't find library libmawt.so needed by debian/jre/usr/java/jre1.7.0_07/lib/amd64/libjawt.so (ELF format: 'elf64-x86-64'; RPATH: '/usr/java/jre1.7.0_07/lib/amd64').
dpkg-shlibdeps: warning: couldn't find library libjvm.so needed by debian/jre/usr/java/jre1.7.0_07/lib/amd64/libjawt.so (ELF format: 'elf64-x86-64'; RPATH: '/usr/java/jre1.7.0_07/lib/amd64').
dpkg-shlibdeps: warning: Can't extract name and version from library name `libawt.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libawt.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libjava.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libjava.so'
dpkg-shlibdeps: warning: couldn't find library libjvm.so needed by debian/jre/usr/java/jre1.7.0_07/lib/amd64/libJdbcOdbc.so (ELF format: 'elf64-x86-64'; RPATH: '/usr/java/jre1.7.0_07/lib/amd64').
dpkg-shlibdeps: warning: Can't extract name and version from library name `libJdbcOdbc.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libJdbcOdbc.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libjava.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libjava.so'
dpkg-shlibdeps: warning: couldn't find library libjvm.so needed by debian/jre/usr/java/jre1.7.0_07/lib/amd64/libfontmanager.so (ELF format: 'elf64-x86-64'; RPATH: '/usr/java/jre1.7.0_07/lib/amd64').
dpkg-shlibdeps: warning: Can't extract name and version from library name `libawt.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libawt.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libjava.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libjava.so'
dpkg-shlibdeps: warning: couldn't find library libjvm.so needed by debian/jre/usr/java/jre1.7.0_07/lib/amd64/libnet.so (ELF format: 'elf64-x86-64'; RPATH: '/usr/java/jre1.7.0_07/lib/amd64').
dpkg-shlibdeps: warning: Can't extract name and version from library name `libjava.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libjava.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libjli.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libjli.so'
dpkg-shlibdeps: warning: couldn't find library libgstreamer-lite.so needed by debian/jre/usr/java/jre1.7.0_07/lib/amd64/fxavcodecplugin-53.so (ELF format: 'elf64-x86-64'; RPATH: '').
dpkg-shlibdeps: error: couldn't find library libavcodec.so.53 needed by debian/jre/usr/java/jre1.7.0_07/lib/amd64/fxavcodecplugin-53.so (ELF format: 'elf64-x86-64'; RPATH: '').
dpkg-shlibdeps: error: couldn't find library libavformat.so.53 needed by debian/jre/usr/java/jre1.7.0_07/lib/amd64/fxavcodecplugin-53.so (ELF format: 'elf64-x86-64'; RPATH: '').
dpkg-shlibdeps: warning: Can't extract name and version from library name `libjli.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libjli.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libjli.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libjli.so'
dpkg-shlibdeps: warning: couldn't find library libjvm.so needed by debian/jre/usr/java/jre1.7.0_07/lib/amd64/libawt.so (ELF format: 'elf64-x86-64'; RPATH: '/usr/java/jre1.7.0_07/lib/amd64').
dpkg-shlibdeps: warning: Can't extract name and version from library name `libjava.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libjava.so'
dpkg-shlibdeps: warning: couldn't find library libjvm.so needed by debian/jre/usr/java/jre1.7.0_07/lib/amd64/libsctp.so (ELF format: 'elf64-x86-64'; RPATH: '/usr/java/jre1.7.0_07/lib/amd64').
dpkg-shlibdeps: warning: Can't extract name and version from library name `libnet.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libnet.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libjava.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libjava.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libnio.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libnio.so'
dpkg-shlibdeps: warning: couldn't find library libjvm.so needed by debian/jre/usr/java/jre1.7.0_07/lib/amd64/libunpack.so (ELF format: 'elf64-x86-64'; RPATH: '/usr/java/jre1.7.0_07/lib/amd64').
dpkg-shlibdeps: warning: Can't extract name and version from library name `libjava.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libjava.so'
dpkg-shlibdeps: warning: couldn't find library libjvm.so needed by debian/jre/usr/java/jre1.7.0_07/lib/amd64/libmlib_image.so (ELF format: 'elf64-x86-64'; RPATH: '/usr/java/jre1.7.0_07/lib/amd64').
dpkg-shlibdeps: warning: Can't extract name and version from library name `libjava.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libjava.so'
dpkg-shlibdeps: warning: couldn't find library libjvm.so needed by debian/jre/usr/java/jre1.7.0_07/lib/amd64/libjsoundalsa.so (ELF format: 'elf64-x86-64'; RPATH: '/usr/java/jre1.7.0_07/lib/amd64').
dpkg-shlibdeps: warning: Can't extract name and version from library name `libjava.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libjava.so'
dpkg-shlibdeps: warning: couldn't find library libjvm.so needed by debian/jre/usr/java/jre1.7.0_07/lib/amd64/libj2gss.so (ELF format: 'elf64-x86-64'; RPATH: '/usr/java/jre1.7.0_07/lib/amd64').
dpkg-shlibdeps: warning: Can't extract name and version from library name `libjava.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libjava.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libjli.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libjli.so'
dpkg-shlibdeps: warning: couldn't find library libgstreamer-lite.so needed by debian/jre/usr/java/jre1.7.0_07/lib/amd64/fxavcodecplugin-52.so (ELF format: 'elf64-x86-64'; RPATH: '').
dpkg-shlibdeps: error: couldn't find library libavcodec.so.52 needed by debian/jre/usr/java/jre1.7.0_07/lib/amd64/fxavcodecplugin-52.so (ELF format: 'elf64-x86-64'; RPATH: '').
dpkg-shlibdeps: error: couldn't find library libavformat.so.52 needed by debian/jre/usr/java/jre1.7.0_07/lib/amd64/fxavcodecplugin-52.so (ELF format: 'elf64-x86-64'; RPATH: '').
dpkg-shlibdeps: warning: couldn't find library libjvm.so needed by debian/jre/usr/java/jre1.7.0_07/lib/amd64/xawt/libmawt.so (ELF format: 'elf64-x86-64'; RPATH: '/usr/java/jre1.7.0_07/lib/amd64/xawt:/usr/java/jre1.7.0_07/lib/amd64/xawt/..').
dpkg-shlibdeps: warning: Can't extract name and version from library name `libawt.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libawt.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libjava.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libjava.so'
dpkg-shlibdeps: warning: couldn't find library libgstreamer-lite.so needed by debian/jre/usr/java/jre1.7.0_07/lib/amd64/fxplugins.so (ELF format: 'elf64-x86-64'; RPATH: '').
dpkg-shlibdeps: warning: dependency on libfontconfig.so.1 could be avoided if "debian/jre/usr/java/jre1.7.0_07/lib/amd64/libglass.so" were not uselessly linked against it (they use none of its symbols).
dpkg-shlibdeps: warning: dependency on libatk-1.0.so.0 could be avoided if "debian/jre/usr/java/jre1.7.0_07/lib/amd64/libglass.so" were not uselessly linked against it (they use none of its symbols).
dpkg-shlibdeps: warning: dependency on libJdbcOdbc.so could be avoided if "debian/jre/usr/java/jre1.7.0_07/lib/amd64/libJdbcOdbc.so" were not uselessly linked against it (they use none of its symbols).
dpkg-shlibdeps: warning: dependency on libpangocairo-1.0.so.0 could be avoided if "debian/jre/usr/java/jre1.7.0_07/lib/amd64/libglass.so" were not uselessly linked against it (they use none of its symbols).
dpkg-shlibdeps: warning: dependency on libfreetype.so.6 could be avoided if "debian/jre/usr/java/jre1.7.0_07/lib/amd64/libglass.so" were not uselessly linked against it (they use none of its symbols).
dpkg-shlibdeps: warning: dependency on libnsl.so.1 could be avoided if "debian/jre/usr/java/jre1.7.0_07/bin/javaws" were not uselessly linked against it (they use none of its symbols).
dpkg-shlibdeps: warning: dependency on librt.so.1 could be avoided if "debian/jre/usr/java/jre1.7.0_07/lib/amd64/libglass.so debian/jre/usr/java/jre1.7.0_07/lib/amd64/libgstplugins-lite.so debian/jre/usr/java/jre1.7.0_07/lib/amd64/fxavcodecplugin-53.so debian/jre/usr/java/jre1.7.0_07/lib/amd64/fxavcodecplugin-52.so debian/jre/usr/java/jre1.7.0_07/lib/amd64/libgstreamer-lite.so debian/jre/usr/java/jre1.7.0_07/lib/amd64/libjfxmedia.so debian/jre/usr/java/jre1.7.0_07/lib/amd64/fxplugins.so" were not uselessly linked against it (they use none of its symbols).
dpkg-shlibdeps: warning: dependency on libpango-1.0.so.0 could be avoided if "debian/jre/usr/java/jre1.7.0_07/lib/amd64/libglass.so" were not uselessly linked against it (they use none of its symbols).
dpkg-shlibdeps: warning: dependency on libXxf86vm.so.1 could be avoided if "debian/jre/usr/java/jre1.7.0_07/lib/amd64/libprism-es2.so" were not uselessly linked against it (they use none of its symbols).
dpkg-shlibdeps: warning: dependency on libpangoft2-1.0.so.0 could be avoided if "debian/jre/usr/java/jre1.7.0_07/lib/amd64/libglass.so" were not uselessly linked against it (they use none of its symbols).
dpkg-shlibdeps: error: Cannot continue due to the errors listed above.
Note: libraries are not searched in other binary packages that do not have any shlibs or symbols file.
To help dpkg-shlibdeps find private libraries, you might need to set LD_LIBRARY_PATH.
dh_shlibdeps: dpkg-shlibdeps -Tdebian/jre.substvars debian/jre/usr/java/jre1.7.0_07/lib/amd64/libjsig.so debian/jre/usr/java/jre1.7.0_07/lib/amd64/libjava_crw_demo.so debian/jre/usr/java/jre1.7.0_07/lib/amd64/libjpeg.so debian/jre/usr/java/jre1.7.0_07/lib/amd64/fxavcodecplugin-53.so debian/jre/usr/java/jre1.7.0_07/lib/amd64/libjavafx-font.so debian/jre/usr/java/jre1.7.0_07/lib/amd64/libdeploy.so debian/jre/usr/java/jre1.7.0_07/lib/amd64/headless/libmawt.so debian/jre/usr/java/jre1.7.0_07/lib/amd64/libnio.so debian/jre/usr/java/jre1.7.0_07/lib/amd64/libgstplugins-lite.so debian/jre/usr/java/jre1.7.0_07/lib/amd64/libjawt.so debian/jre/usr/java/jre1.7.0_07/lib/amd64/libverify.so debian/jre/usr/java/jre1.7.0_07/lib/amd64/libjaas_unix.so debian/jre/usr/java/jre1.7.0_07/lib/amd64/libjfxwebkit.so debian/jre/usr/java/jre1.7.0_07/lib/amd64/libnet.so debian/jre/usr/java/jre1.7.0_07/lib/amd64/libjavafx-iio.so debian/jre/usr/java/jre1.7.0_07/lib/amd64/libinstrument.so debian/jre/usr/java/jre1.7.0_07/lib/amd64/libglass.so debian/jre/usr/java/jre1.7.0_07/lib/amd64/libjfr.so debian/jre/usr/java/jre1.7.0_07/lib/amd64/libdt_socket.so debian/jre/usr/java/jre1.7.0_07/lib/amd64/libunpack.so debian/jre/usr/java/jre1.7.0_07/lib/amd64/jli/libjli.so debian/jre/usr/java/jre1.7.0_07/lib/amd64/libkcms.so debian/jre/usr/java/jre1.7.0_07/lib/amd64/libjsound.so debian/jre/usr/java/jre1.7.0_07/lib/amd64/libnpt.so debian/jre/usr/java/jre1.7.0_07/lib/amd64/libj2pkcs11.so debian/jre/usr/java/jre1.7.0_07/lib/amd64/xawt/libmawt.so debian/jre/usr/java/jre1.7.0_07/lib/amd64/libJdbcOdbc.so debian/jre/usr/java/jre1.7.0_07/lib/amd64/libjsoundalsa.so debian/jre/usr/java/jre1.7.0_07/lib/amd64/libt2k.so debian/jre/usr/java/jre1.7.0_07/lib/amd64/fxplugins.so debian/jre/usr/java/jre1.7.0_07/lib/amd64/librmi.so debian/jre/usr/java/jre1.7.0_07/lib/amd64/libsctp.so debian/jre/usr/java/jre1.7.0_07/lib/amd64/fxavcodecplugin-52.so debian/jre/usr/java/jre1.7.0_07/lib/amd64/libmanagement.so debian/jre/usr/java/jre1.7.0_07/lib/amd64/libjava.so debian/jre/usr/java/jre1.7.0_07/lib/amd64/libfontmanager.so debian/jre/usr/java/jre1.7.0_07/lib/amd64/libsplashscreen.so debian/jre/usr/java/jre1.7.0_07/lib/amd64/libgstreamer-lite.so debian/jre/usr/java/jre1.7.0_07/lib/amd64/libzip.so debian/jre/usr/java/jre1.7.0_07/lib/amd64/libjdwp.so debian/jre/usr/java/jre1.7.0_07/lib/amd64/libawt.so debian/jre/usr/java/jre1.7.0_07/lib/amd64/libjavaplugin_jni.so debian/jre/usr/java/jre1.7.0_07/lib/amd64/server/libjvm.so debian/jre/usr/java/jre1.7.0_07/lib/amd64/libmlib_image.so debian/jre/usr/java/jre1.7.0_07/lib/amd64/libjfxmedia.so debian/jre/usr/java/jre1.7.0_07/lib/amd64/libjsdt.so debian/jre/usr/java/jre1.7.0_07/lib/amd64/libdcpr.so debian/jre/usr/java/jre1.7.0_07/lib/amd64/libhprof.so debian/jre/usr/java/jre1.7.0_07/lib/amd64/libsunec.so debian/jre/usr/java/jre1.7.0_07/lib/amd64/libprism-es2.so debian/jre/usr/java/jre1.7.0_07/lib/amd64/libnpjp2.so debian/jre/usr/java/jre1.7.0_07/lib/amd64/libj2gss.so debian/jre/usr/java/jre1.7.0_07/lib/amd64/libj2pcsc.so debian/jre/usr/java/jre1.7.0_07/lib/jexec debian/jre/usr/java/jre1.7.0_07/bin/orbd debian/jre/usr/java/jre1.7.0_07/bin/rmiregistry debian/jre/usr/java/jre1.7.0_07/bin/unpack200 debian/jre/usr/java/jre1.7.0_07/bin/servertool debian/jre/usr/java/jre1.7.0_07/bin/javaws debian/jre/usr/java/jre1.7.0_07/bin/tnameserv debian/jre/usr/java/jre1.7.0_07/bin/keytool debian/jre/usr/java/jre1.7.0_07/bin/policytool debian/jre/usr/java/jre1.7.0_07/bin/java debian/jre/usr/java/jre1.7.0_07/bin/pack200 debian/jre/usr/java/jre1.7.0_07/bin/rmid debian/jre/usr/java/jre1.7.0_07/bin/java_vm returned exit code 2
make: [binary-arch] Error 9 (ignored)
dh_gencontrol
dpkg-gencontrol: warning: Depends field of package jre: unknown substitution variable ${shlibs:Depends}
dh_md5sums
dh_builddeb
dpkg-deb: error: parsing file 'debian/jre/DEBIAN/control' near line 2 package 'jre':
 error in Version string '1.7.0_07-1': invalid character in version number
dh_builddeb: dpkg-deb --build debian/jre .. returned exit code 2
make: *** [binary-arch] Error 9
allexander@ubuntu:~$
```

---

### Post by holycow131415 on 2012-10-16
Search the forums dude.

[http://ubuntuforums.org/showpost.php?p=12292059&postcount=2](http://ubuntuforums.org/showpost.php?p=12292059&postcount=2)

> **Lyfang said:**
> Try adding the following repository found from: [http://www.webupd8.org/2012/01/install-oracle-java-jdk-7-in-ubuntu-via.html](http://www.webupd8.org/2012/01/install-oracle-java-jdk-7-in-ubuntu-via.html) (supports Ubuntu 12.04, 11.10, 11.04 and 10.04): 
```
sudo add-apt-repository ppa:webupd8team/java
sudo apt-get update
sudo apt-get install oracle-java7-installer
```or
```
sudo rm /var/lib/dpkg/info/oracle-java7-installer* sudo apt-get  purge oracle-java7-installer* sudo rm /etc/apt/sources.list.d/*java*  sudo apt-get update sudo add-apt-repository ppa:webupd8team/java sudo  apt-get update sudo apt-get install oracle-java7-installer
```Thread  can still be useful, applies to Ubuntu 12.04. See also: [Ubuntu 12.04 Java Failed Install]("http://ubuntuforums.org/showthread.php?t=1977483")

---

### Post by QIII on 2012-10-16
holycow's suggestion is given in the wiki in my signature under Oracle Java 7, "Command line methods", and the link "Using webupd8.org's strikingly simple method."

There is some other good info about Java there, too.

holycow -- I prefer to direct people to the wikis to show them the resources are there and because there has been a lot of work done to move all of the forum "How tos" to the community wikis.  The wikis are updateable where posts may become dated after some time.

---

