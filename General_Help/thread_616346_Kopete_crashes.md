---
title: "Kopete crashes"
date: 2007-11-18
forum: General Help
---

### Post by joebanana on 2007-11-18
Having problem with kopete in 7.10. It worked fine in 7.04. I install kopete it logs on, can receive messages but if i type something and hit enter it crashes and i have to force quit.

```


rok@rok-desktop:~$ kopete
kbuildsycoca running...
Reusing existing ksycoca
rok@rok-desktop:~$ kdecore (KLibLoader): WARNING: KLibrary: /usr/lib/libcrypto.so.0.9.8: undefined symbol: PKCS7_content_free
kdecore (KLibLoader): WARNING: KLibrary: /usr/lib/libcrypto.so.0.9.8: undefined symbol: OpenSSL_add_all_algorithms
kdecore (KLibLoader): WARNING: KLibrary: /usr/lib/libcrypto.so.0.9.8: undefined symbol: OPENSSL_add_all_algorithms
kdecore (KLibLoader): WARNING: KLibrary: /usr/lib/libcrypto.so.0.9.8: undefined symbol: OpenSSL_add_all_algorithms_conf
kdecore (KLibLoader): WARNING: KLibrary: /usr/lib/libcrypto.so.0.9.8: undefined symbol: PKCS7_content_free
kdecore (KLibLoader): WARNING: KLibrary: /usr/lib/libcrypto.so.0.9.8: undefined symbol: OpenSSL_add_all_algorithms
kdecore (KLibLoader): WARNING: KLibrary: /usr/lib/libcrypto.so.0.9.8: undefined symbol: OPENSSL_add_all_algorithms
kdecore (KLibLoader): WARNING: KLibrary: /usr/lib/libcrypto.so.0.9.8: undefined symbol: OpenSSL_add_all_algorithms_conf
QFont::setPointSize: Point size <= 0 (-1)
QFont::setPointSize: Point size <= 0 (-1)
X Error: BadWindow (invalid Window parameter) 3
  Major opcode:  7
  Minor opcode:  0
  Resource id:  0x2400053
ICE default IO error handler doing an exit(), pid = 14107, errno = 0


```

---

### Post by alphablue52 on 2007-12-30
Hi,

got the same problem after Gutsy upgrade - somethimes when a KDE app (konqueror, kopete, ...) wants to access to kwallet, it hangs up, and the kded proccess runs on 100% CPU.
Error message:

```
kdecore (KLibLoader): WARNING: KLibrary: /usr/lib/libcrypto.so.0.9.8: undefined symbol: PKCS7_content_free
kdecore (KLibLoader): WARNING: KLibrary: /usr/lib/libcrypto.so.0.9.8: undefined symbol: OpenSSL_add_all_algorithms
kdecore (KLibLoader): WARNING: KLibrary: /usr/lib/libcrypto.so.0.9.8: undefined symbol: OPENSSL_add_all_algorithms
kdecore (KLibLoader): WARNING: KLibrary: /usr/lib/libcrypto.so.0.9.8: undefined symbol: OpenSSL_add_all_algorithms_conf

```

Google gave me a hit at a Gentoo forum (these geeks ;-) at looks like a version problem between kde and openssl.
I have no solution jet, just "pkill -9 kded" and restart it :-(

Guess you can post a Launchpad Bug for that

Cheers
Torsten.

---

### Post by Mekk on 2008-01-25
I feel there is some conflict between libraries.

I installed kubuntu gutsy recently and it worked without problems.

Then I installed a bunch of additional libraries (for development purposes), including openssl development and libraries, mcrypto dev and ... many others.

And then this problem suddenly started to occur.

I see exactly the same - kded freezes so wallet does not work (and many other apps), aforementioned warnings about undefined symbols in xsession-errors (and kded restart  resolves the problems).

---

