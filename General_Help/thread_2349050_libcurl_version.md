---
title: "libcurl version?"
date: 2017-01-10
forum: General Help
---

### Post by rebeltaz on 2017-01-10
I am trying to build the transmission bittorrent client, but configure is complaining:

```

checking for LIBCURL... configure: error: Package requirements (libcurl >= 7.15.4) were not met:

No package 'libcurl' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables LIBCURL_CFLAGS
and LIBCURL_LIBS to avoid the need to call pkg-config.

```

When I run a search on dpkg, I get this:

```

derek@shop:~/downloads/transmission-2.82$ dpkg -l | grep libcurl
ii  libcurl3                              7.19.7-1ubuntu1.11                              Multi-protocol file transfer library (OpenSS
ii  libcurl3-gnutls                       7.19.7-1ubuntu1.11                              Multi-protocol file transfer library (GnuTLS
ii  python-pycurl                         7.19.0-3                                        Python bindings to libcurl

```

Is my current version not greater than the required version?

---

### Post by steeldriver on 2017-01-10
What version of Ubuntu is this?

Usually, builds from source require the corresponding development package headers - not just the runtime library package

In the case of libcurl, IIRC the dev package is virtual, and you will need to choose one of gnutls, openssl, nss implementations e.g. on my 16.04 system the options are

```

libcurl4-gnutls-dev - development files and documentation for libcurl (GnuTLS flavour)
libcurl4-nss-dev - development files and documentation for libcurl (NSS flavour)
libcurl4-openssl-dev - development files and documentation for libcurl (OpenSSL flavour)

```

---

### Post by rebeltaz on 2017-01-10
This is 10.04 LTS. And apt-cache search shows:

```

derek@shop:~/downloads/transmission-2.82$ apt-cache search libcurl
python-pycurl - Python bindings to libcurl
python-pycurl-dbg - Python bindings to libcurl (debug extension)
libcurl-ocaml - OCaml curl bindings (Runtime Library)
libcurl-ocaml-dev - OCaml libcurl bindings (Development package)
libghc6-curl-dev - GHC 6 libraries for the libcurl Haskell bindings
libghc6-curl-doc - Documentation for the libcurl Haskell bindings
libghc6-curl-prof - Profiling libraries for the libcurl Haskell bindings
liblua5.1-curl-dev - libcURL development files for the Lua language version 5.1
liblua5.1-curl0 - libcURL bindings for the Lua language version 5.1
libwww-curl-perl - Perl bindings to libcurl
tclcurl - Tcl bindings to libcurl
wmget - Background download manager in a Window Maker dock app
gnupg - GNU privacy guard - a free PGP replacement
gnupg-curl - GNU privacy guard - a free PGP replacement (cURL)
libcurl3 - Multi-protocol file transfer library (OpenSSL)
libcurl3-dbg - libcurl compiled with debug symbols
libcurl3-gnutls - Multi-protocol file transfer library (GnuTLS)
libcurl4-gnutls-dev - Development files and documentation for libcurl (GnuTLS)
libcurl4-openssl-dev - Development files and documentation for libcurl (OpenSSL)
fp-units-net - Free Pascal - networking units

```

So I need to install
```

libcurl4-gnutls-dev - Development files and documentation for libcurl (GnuTLS)
libcurl4-openssl-dev - Development files and documentation for libcurl (OpenSSL)

```
?

---

### Post by rebeltaz on 2017-01-12
OK... so installing those files fixed that problem. Now it's complaining about libevent.

```

checking for LIBEVENT... configure: error: Package requirements (libevent >= 2.0.10) were not met:

No package 'libevent' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables LIBEVENT_CFLAGS
and LIBEVENT_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

```

I installed libevent-dev, and I do seem to have a 2.0.10 installed as well as the 1.4-2 version:

```

derek@shop:~/downloads/transmission-2.82$ dpkg -l | grep libevent
ii  libevent-1.4-2                        1.4.13-stable-1ubuntu0.1                        An asynchronous event notification library
rc  libevent-2.0-5                        2.0.10-stable-1ubuntu0.10.04.2                  An asynchronous event notification library
ii  libevent-core-1.4-2                   1.4.13-stable-1ubuntu0.1                        An asynchronous event notification library (
ii  libevent-dev                          1.4.13-stable-1ubuntu0.1                        Development libraries, header files and docs
ii  libevent-extra-1.4-2                  1.4.13-stable-1ubuntu0.1                        An asynchronous event notification library (

```

How do I make .configure see the newer version?

---

