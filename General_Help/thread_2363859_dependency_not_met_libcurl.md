---
title: "dependency not met: libcurl"
date: 2017-06-15
forum: General Help
---

### Post by Achilles124 on 2017-06-15
I am trying to install the game alien arena on my system (Ubuntu 16.10). I had installed it by way of the repositories, but there is a bug in it that doesn't allow to play in single player mode.

That is why I decided to install it by way of ./configure, make, make install.

This is the message that I get when I try to install this way:
> configure: error: Package requirements (libcurl ogg vorbis vorbisfile freetype2) were not met:

No package 'libcurl' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables DEPS_CFLAGS
and DEPS_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.


Problem is that there are many libcurl packages in the repositories. See for the list:
[https://launchpad.net/ubuntu/yakkety/+source/curl](https://launchpad.net/ubuntu/yakkety/+source/curl)
curl: command line tool for transferring data with URL syntax
curl-dbgsym: debug symbols for package curl
libcurl3: easy-to-use client-side URL transfer library (OpenSSL flavour)
libcurl3-dbg: debugging symbols for libcurl (OpenSSL, GnuTLS and NSS flavours)
libcurl3-dbgsym: debug symbols for package libcurl3
libcurl3-gnutls: easy-to-use client-side URL transfer library (GnuTLS flavour)
libcurl3-gnutls-dbgsym: debug symbols for package libcurl3-gnutls
libcurl3-nss: easy-to-use client-side URL transfer library (NSS flavour)
libcurl3-nss-dbgsym: debug symbols for package libcurl3-nss
libcurl4-doc: documentation for libcurl
libcurl4-gnutls-dev: development files and documentation for libcurl (GnuTLS flavour)
libcurl4-gnutls-dev-dbgsym: debug symbols for package libcurl4-gnutls-dev
libcurl4-nss-dev: development files and documentation for libcurl (NSS flavour)
libcurl4-nss-dev-dbgsym: debug symbols for package libcurl4-nss-dev
libcurl4-openssl-dev: development files and documentation for libcurl (OpenSSL flavour)
libcurl4-openssl-dev-dbgsym: debug symbols for package libcurl4-openssl-dev

What package do I need? Or how do I figure that out?

---

### Post by oldos2er on 2017-06-15
```
sudo apt-get build-dep alien-arena 
``` assuming alien-arena is the correct package name.

---

### Post by Achilles124 on 2017-06-16
That worked. Thank you.

---

### Post by oldos2er on 2017-06-16
Welcome, and thank you for marking the thread solved.

---

