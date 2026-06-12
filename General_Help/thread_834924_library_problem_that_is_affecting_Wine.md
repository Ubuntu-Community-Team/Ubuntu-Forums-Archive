---
title: "library problem that is affecting Wine"
date: 2008-06-19
forum: General Help
---

### Post by portlandor on 2008-06-19
Hi,

I am running Hardy with wine 1.0.0~winehq-ubuntu~8.04-1. I am posting this here as I don't think its a Wine specific problem.  That forum had no answers for me, nor did a search of Ubuntu forums or Google.

Looks like some sort of library problem.  I reinstalled libc and still get the errors.

Thanks,  Rob.



/usr/bin/wine: /usr/bin/../lib/libc.so.6: no version information available (required by /usr/bin/wine)
/usr/bin/wine: /usr/bin/../lib/libc.so.6: no version information available (required by /usr/bin/wine)
/usr/bin/wine: /usr/bin/../lib/libc.so.6: no version information available (required by /usr/bin/wine)~
/usr/bin/wine: /usr/bin/../lib/libc.so.6: no version information available (required by /usr/bin/../lib/libwine.so.1)
/usr/bin/wine: /usr/bin/../lib/libc.so.6: no version information available (required by /usr/bin/../lib/libwine.so.1)
/usr/bin/wine: /usr/bin/../lib/libc.so.6: no version information available (required by /usr/bin/../lib/libwine.so.1)
/usr/bin/wine: /usr/bin/../lib/libc.so.6: no version information available (required by /usr/bin/../lib/libwine.so.1)
/usr/bin/wine: /usr/bin/../lib/libc.so.6: no version information available (required by /usr/bin/../lib/libwine.so.1)
/usr/bin/wine: /usr/bin/../lib/libc.so.6: no version information available (required by /usr/bin/../lib/libwine.so.1)
/usr/bin/wine: /usr/bin/../lib/libc.so.6: no version information available (required by /lib/tls/i686/cmov/libpthread.so.0)
/usr/bin/wine: /usr/bin/../lib/libc.so.6: no version information available (required by /lib/tls/i686/cmov/libpthread.so.0)
/usr/bin/wine: /usr/bin/../lib/libc.so.6: no version information available (required by /lib/tls/i686/cmov/libpthread.so.0)
/usr/bin/wine: /usr/bin/../lib/libc.so.6: no version information available (required by /lib/tls/i686/cmov/libpthread.so.0)
/usr/bin/wine: /usr/bin/../lib/libc.so.6: no version information available (required by /lib/tls/i686/cmov/libpthread.so.0)
/usr/bin/wine: /usr/bin/../lib/libc.so.6: no version information available (required by /lib/tls/i686/cmov/libpthread.so.0)
/usr/bin/wine: /usr/bin/../lib/libc.so.6: no version information available (required by /usr/bin/../lib/libc.so.6)
/usr/bin/wine: /usr/bin/../lib/libc.so.6: no version information available (required by /usr/bin/../lib/libc.so.6)
/usr/bin/wine: /usr/bin/../lib/libc.so.6: no version information available (required by /usr/bin/../lib/libc.so.6)
/usr/bin/wine: /usr/bin/../lib/libc.so.6: no version information available (required by /usr/bin/../lib/libc.so.6)
/usr/bin/wine: /usr/bin/../lib/libc.so.6: no version information available (required by /usr/bin/../lib/libc.so.6)
/usr/bin/wine: /usr/bin/../lib/libc.so.6: no version information available (required by /lib/tls/i686/cmov/libdl.so.2)
/usr/bin/wine: /usr/bin/../lib/libc.so.6: no version information available (required by /lib/tls/i686/cmov/libdl.so.2)
/usr/bin/wine: /usr/bin/../lib/libc.so.6: no version information available (required by /lib/tls/i686/cmov/libdl.so.2)
/usr/bin/wine: /usr/bin/../lib/libc.so.6: no version information available (required by /lib/tls/i686/cmov/libdl.so.2)
/usr/bin/wine: relocation error: /lib/tls/i686/cmov/libdl.so.2: symbol _libc_intl_domainname, version GLIBC_2.0 not defined in file libc.so.6 with link time reference

---

### Post by VMC on 2008-06-20
What are you trying to run. Will anything run under Wine? Did you try running using the Terminal and Wine?

---

