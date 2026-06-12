---
title: "sluggish SSH - glibc error reports"
date: 2008-04-24
forum: General Help
---

### Post by dbrooke on 2008-04-24
Hello, I am doing some WebSite maintenance on a customers Fedora server ...(yes, I know, but I personally use ubuntu and I like you guys better ;-) )... and I am seeing this situation:

Logged on via SSH
pretty sluggish typing (not usual for this server)
The sluggishness grows pretty much to a freeze...
then the console spits out a glibc report like:

*** glibc detected *** WebCatalog: malloc(): memory corruption: 0xb05211d8 ***
======= Backtrace: =========
/lib/libc.so.6[0xb78df1a2]
/lib/libc.so.6(malloc+0x74)[0xb78e0587]
/lib/libc.so.6(open_memstream+0x20)[0xb78d6d2c]
/lib/libc.so.6(vsyslog+0x2a4)[0xb7941bf9]
/lib/libc.so.6(syslog+0x22)[0xb7941ef8]
WebCatalog[0x810ad02]
WebCatalog[0x805824b]
WebCatalog(vfprintf+0x37b8)[0x8056fac]
[0xffffe420]
WebCatalog[0x810aad2]

etc...
[snip]

Then it goes back to regular sluggishness and does it all over again.. (on about 10 min. intervals)

If anything can be gleaned from my description, any comments would be much appreciated as my linux administration abilities are not that good!

Thanks,
Donovan

P.S. WebCatalog is a server-side app kinda like PHP (which I am familiar with).

---

