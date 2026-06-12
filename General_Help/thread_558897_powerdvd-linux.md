---
title: "powerdvd-linux"
date: 2007-09-24
forum: General Help
---

### Post by mobius357 on 2007-09-24
This isn't the question you're all probably expecting. I came accross this: [http://www.bluesquad.com/usa/prod.php?pid=1989#features](http://www.bluesquad.com/usa/prod.php?pid=1989#features) and I figured for 19 bucks it can't hurt to try. Anyway, the DL comes as an rpm which I tried to convert with alien, only that didn't work. It gave my this log:

```
sudo alien -d powerdvd-fuji.i386.rpm
Warning: Skipping conversion of scripts in package powerdvd: postinst
Warning: Use the --scripts parameter to include the scripts.
Package build failed. Here's the log:
dh_testdir
dh_testdir
dh_testroot
dh_clean -k -d
dh_installdirs
dh_installdocs
dh_installchangelogs
find . -maxdepth 1 -mindepth 1 -not -name debian -print0 | \
                xargs -0 -r -i cp -a {} debian/powerdvd
dh_compress
dh_makeshlibs
dh_installdeb
dh_shlibdeps
dpkg-shlibdeps: warning: unable to find dependency information for shared library libSDL-1.2 (soname 0, path libSDL-1.2.so.0, dependency field Depends)
dpkg-shlibdeps: warning: could not find any packages for libImlib.so.11
dpkg-shlibdeps: warning: unable to find dependency information for shared library libImlib (soname 11, path libImlib.so.11, dependency field Depends)
dpkg-shlibdeps: warning: could not find any packages for libgtk-1.2.so.0
dpkg-shlibdeps: warning: unable to find dependency information for shared library libgtk-1.2 (soname 0, path libgtk-1.2.so.0, dependency field Depends)
dpkg-shlibdeps: warning: could not find any packages for libgdk-1.2.so.0
dpkg-shlibdeps: warning: unable to find dependency information for shared library libgdk-1.2 (soname 0, path libgdk-1.2.so.0, dependency field Depends)
dpkg-shlibdeps: warning: could not find any packages for libgmodule-1.2.so.0
dpkg-shlibdeps: warning: unable to find dependency information for shared library libgmodule-1.2 (soname 0, path libgmodule-1.2.so.0, dependency field Depends)
dpkg-shlibdeps: warning: could not find any packages for libglib-1.2.so.0
dpkg-shlibdeps: warning: unable to find dependency information for shared library libglib-1.2 (soname 0, path libglib-1.2.so.0, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libXi (soname 6, path libXi.so.6, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libXext (soname 6, path libXext.so.6, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libX11 (soname 6, path libX11.so.6, dependency field Depends)
dpkg-shlibdeps: warning: could not find any packages for libgdk_imlib.so.1
dpkg-shlibdeps: warning: unable to find dependency information for shared library libgdk_imlib (soname 1, path libgdk_imlib.so.1, dependency field Depends)
dpkg-shlibdeps: warning: could not find any packages for libgdk_pixbuf.so.2
dpkg-shlibdeps: warning: unable to find dependency information for shared library libgdk_pixbuf (soname 2, path libgdk_pixbuf.so.2, dependency field Depends)
dpkg-shlibdeps: warning: could not find any packages for libXv.so.1
dpkg-shlibdeps: warning: unable to find dependency information for shared library libXv (soname 1, path libXv.so.1, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 5, path libstdc++.so.5, dependency field Depends)
dh_gencontrol
dpkg-gencontrol: error: current build architecture amd64 does not appear in package's list (i386)
dh_gencontrol: command returned error code 65280
make: *** [binary-arch] Error 1
find: powerdvd-3.00: No such file or directory
```

I tried again adding the --scripts with no effect to my untrained eye

```
sudo alien -d powerdvd-fuji.i386.rpm --scripts
Package build failed. Here's the log:
dh_testdir
dh_testdir
dh_testroot
dh_clean -k -d
dh_installdirs
dh_installdocs
dh_installchangelogs
find . -maxdepth 1 -mindepth 1 -not -name debian -print0 | \
                xargs -0 -r -i cp -a {} debian/powerdvd
dh_compress
dh_makeshlibs
dh_installdeb
dh_shlibdeps
dpkg-shlibdeps: warning: unable to find dependency information for shared library libSDL-1.2 (soname 0, path libSDL-1.2.so.0, dependency field Depends)
dpkg-shlibdeps: warning: could not find any packages for libImlib.so.11
dpkg-shlibdeps: warning: unable to find dependency information for shared library libImlib (soname 11, path libImlib.so.11, dependency field Depends)
dpkg-shlibdeps: warning: could not find any packages for libgtk-1.2.so.0
dpkg-shlibdeps: warning: unable to find dependency information for shared library libgtk-1.2 (soname 0, path libgtk-1.2.so.0, dependency field Depends)
dpkg-shlibdeps: warning: could not find any packages for libgdk-1.2.so.0
dpkg-shlibdeps: warning: unable to find dependency information for shared library libgdk-1.2 (soname 0, path libgdk-1.2.so.0, dependency field Depends)
dpkg-shlibdeps: warning: could not find any packages for libgmodule-1.2.so.0
dpkg-shlibdeps: warning: unable to find dependency information for shared library libgmodule-1.2 (soname 0, path libgmodule-1.2.so.0, dependency field Depends)
dpkg-shlibdeps: warning: could not find any packages for libglib-1.2.so.0
dpkg-shlibdeps: warning: unable to find dependency information for shared library libglib-1.2 (soname 0, path libglib-1.2.so.0, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libXi (soname 6, path libXi.so.6, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libXext (soname 6, path libXext.so.6, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libX11 (soname 6, path libX11.so.6, dependency field Depends)
dpkg-shlibdeps: warning: could not find any packages for libgdk_imlib.so.1
dpkg-shlibdeps: warning: unable to find dependency information for shared library libgdk_imlib (soname 1, path libgdk_imlib.so.1, dependency field Depends)
dpkg-shlibdeps: warning: could not find any packages for libgdk_pixbuf.so.2
dpkg-shlibdeps: warning: unable to find dependency information for shared library libgdk_pixbuf (soname 2, path libgdk_pixbuf.so.2, dependency field Depends)
dpkg-shlibdeps: warning: could not find any packages for libXv.so.1
dpkg-shlibdeps: warning: unable to find dependency information for shared library libXv (soname 1, path libXv.so.1, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 5, path libstdc++.so.5, dependency field Depends)
dh_gencontrol
dpkg-gencontrol: error: current build architecture amd64 does not appear in package's list (i386)
dh_gencontrol: command returned error code 65280
make: *** [binary-arch] Error 1
find: powerdvd-3.00: No such file or directory
```

I'm new to linux so I haven't a clue if theres anything to be done with this and if there isnt I'm only out 19 bucks so no big deal.

---

### Post by xcube on 2007-10-02
I got it to error out.

I did:
1. alien --scripts --to-tgz powerdvd-fuji.i386.rpm     # convert rpm to tgz
2. cd /tmp/safeplace ; tar zxvf powerdvd-3.00.tgz   # dump tgz somewhere safe
3. ldd /tmp/safeplace/usr/local/pdvd/pdvd    # get list of shared libs + missing libs
4. Found missing libraries, copied them to /usr/local/lib32, and added LD_LIBRARY_PATH=/usr/local/lib32 to ~/.bashrc

The result:
user@tool:/usr/local/pdvd$ pdvd
gdk_imlib ERROR: Cannot load image: .//skinfile/oscar/ui_base.bmp
All fallbacks failed.

The path .//skinfile/oscar/ui_base.bmp is ok.

It should be doable....

---

### Post by xcube on 2007-10-02
strace results (attached) show many file open errors.
It looks harder now...

pdvd: ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), for GNU/Linux 2.2.5, dynamically linked (uses shared libs), stripped

---

### Post by xcube on 2007-10-03
More progress.
I added missing libimlib-bmp.so , not mentioned by ldd.
Intro screen flashes, then it exits with following:

xcube@tool:/usr/local/pdvd$ pdvd
** CRITICAL **: file gdk-pixbuf.c: line 347 (gdk_pixbuf_get_height): assertion `pixbuf != NULL' failed.
** CRITICAL **: file gdk-pixbuf.c: line 331 (gdk_pixbuf_get_width): assertion `pixbuf != NULL' failed.
** CRITICAL **: file gdk-pixbuf.c: line 347 (gdk_pixbuf_get_height): assertion `pixbuf != NULL' failed.
.......
** CRITICAL **: file gdk-pixbuf.c: line 331 (gdk_pixbuf_get_width): assertion `pixbuf != NULL' failed.
find elem error.
Gdk-ERROR **: BadMatch (invalid parameter attributes)
  serial 344 error_code 8 request_code 2 minor_code 0

---

### Post by xcube on 2007-10-03
/usr/lib/X11R6 32-bit shared libs were missing, added them.
gdb stack trace shows crash in libXcursor.so

** CRITICAL **: file gdk-pixbuf.c: line 331 (gdk_pixbuf_get_width): assertion `pixbuf != NULL' failed.
[New Thread 4137126800 (LWP 5798)]
find elem error.
Gdk-ERROR **: BadMatch
  serial 322 error_code 8 request_code 2 minor_code 0
[Thread 4137126800 (LWP 5798) exited]

Program received signal SIGSEGV, Segmentation fault.
[Switching to Thread 4152145600 (LWP 5794)]
0xf6e09ab9 in ?? () from /usr/X11R6/lib32/libXcursor.so.1.0
(gdb) where
#0  0xf6e09ab9 in ?? () from /usr/X11R6/lib32/libXcursor.so.1.0
#1  0x007bec24 in ?? ()
#2  0x00000000 in ?? ()
(gdb)

---

