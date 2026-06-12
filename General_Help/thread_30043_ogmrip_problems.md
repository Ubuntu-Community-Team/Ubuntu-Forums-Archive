---
title: "ogmrip problems"
date: 2005-04-27
forum: General Help
---

### Post by hill on 2005-04-27
Im trying to compile ogmrip and I get an error . any ideas?

thanks for any help.
```

hill@ubuntu:~/Desktop/ogmrip-0.8.1$ make
make  all-recursive
make[1]: Entering directory `/home/hill/Desktop/ogmrip-0.8.1'
Making all in libogmdvd
make[2]: Entering directory `/home/hill/Desktop/ogmrip-0.8.1/libogmdvd'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/hill/Desktop/ogmrip-0.8.1/libogmdvd'
Making all in libogmspawn
make[2]: Entering directory `/home/hill/Desktop/ogmrip-0.8.1/libogmspawn'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/hill/Desktop/ogmrip-0.8.1/libogmspawn'
Making all in libogmrip
make[2]: Entering directory `/home/hill/Desktop/ogmrip-0.8.1/libogmrip'
/bin/sh ../libtool --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I.. -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include    -I../libogmspawn -I../libogmdvd    -g -O2 -I/usr/local/include -Wall -Werror -I.. -c ogmrip-backend.c
 gcc -DHAVE_CONFIG_H -I. -I. -I.. -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I../libogmspawn -I../libogmdvd -g -O2 -I/usr/local/include -Wall -Werror -I.. -c ogmrip-backend.c  -fPIC -DPIC -o .libs/ogmrip-backend.o
cc1: warnings being treated as errors
ogmrip-backend.c: In function 'ogmrip_backend_wav_command':
ogmrip-backend.c:308: warning: pointer targets in passing argument 2 of 'ogmrip_codec_get_chapters' differ in signedness
ogmrip-backend.c:308: warning: pointer targets in passing argument 3 of 'ogmrip_codec_get_chapters' differ in signedness
ogmrip-backend.c: In function 'ogmrip_backend_acopy_command':
ogmrip-backend.c:377: warning: pointer targets in passing argument 2 of 'ogmrip_codec_get_chapters' differ in signedness
ogmrip-backend.c:377: warning: pointer targets in passing argument 3 of 'ogmrip_codec_get_chapters' differ in signedness
ogmrip-backend.c: In function 'ogmrip_backend_xvid_command':
ogmrip-backend.c:646: warning: pointer targets in passing argument 2 of 'ogmrip_codec_get_chapters' differ in signedness
ogmrip-backend.c:646: warning: pointer targets in passing argument 3 of 'ogmrip_codec_get_chapters' differ in signedness
ogmrip-backend.c: In function 'ogmrip_backend_lavc_command':
ogmrip-backend.c:752: warning: pointer targets in passing argument 2 of 'ogmrip_codec_get_chapters' differ in signedness
ogmrip-backend.c:752: warning: pointer targets in passing argument 3 of 'ogmrip_codec_get_chapters' differ in signedness
ogmrip-backend.c: In function 'ogmrip_backend_vobsub_command':
ogmrip-backend.c:1368: warning: pointer targets in passing argument 2 of 'ogmrip_codec_get_chapters' differ in signedness
ogmrip-backend.c:1368: warning: pointer targets in passing argument 3 of 'ogmrip_codec_get_chapters' differ in signedness
make[2]: *** [ogmrip-backend.lo] Error 1
make[2]: Leaving directory `/home/hill/Desktop/ogmrip-0.8.1/libogmrip'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/hill/Desktop/ogmrip-0.8.1'
make: *** [all-recursive-am] Error 2
hill@ubuntu:~/Desktop/ogmrip-0.8.1$

```

---

### Post by steffen on 2005-05-04
Have you installed all dependancies, including the dev-parts?

I just compiled and installed ogmrip 8.2 successfuly in Hoary.

---

### Post by Sniffer on 2005-05-20
[QUOTE=steffen]Have you installed all dependancies, including the dev-parts?

I just compiled and installed ogmrip 8.2 successfuly in Hoary.[/QUOTE]


How do you install mplayer???

I have tried ./configure with OGMRIP 8.2 but it tells me that mplayer was not configured with XVID support and OGMRIP needs XVID support.....

Thks.

---

### Post by Pink Chick on 2005-06-02
[QUOTE=steffen]Have you installed all dependancies, including the dev-parts?

I just compiled and installed ogmrip 8.2 successfuly in Hoary.[/QUOTE]
 Yes, tell us please. I would love to have ore create a debian package. I did one for archlinux, what has an really easy to handle package system, and never tried to do debian packages before. So compiling tricks should be the first step, before fighting the unknown packatizing war.

---

### Post by rupert on 2005-07-18
I just compiled it, but it hasnt created any executable.
Can someone please post the package names that i need to install under hoary to get it running, the official forums and docs dont really help.
Maybe someone created a hoary conform .deb with checkinstall


htx

---

