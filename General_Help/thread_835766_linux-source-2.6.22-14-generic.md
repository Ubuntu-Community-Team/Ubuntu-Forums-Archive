---
title: "linux-source-2.6.22-14-generic??"
date: 2008-06-20
forum: General Help
---

### Post by brettw.10 on 2008-06-20
Hi guys,

I am currently trying to compile sasc-ng for my Mythbuntu 7.10 release, and it mentions that I need the following links set up:

/lib/modules/`uname -r`/build
/lib/modules/`uname -r`/source

In my case, the "build" link points to /usr/src/linux-headers-2.6.22-14-generic and I assume that I should build the missing "source" link to /usr/src/linux-source-2.6.22-14-generic.  Problem is that this doesn't exist.

I have already apt-get'd linux-source and linux-source-2.6.22, but I cannot find a linux-source-2.6.22-generic or anything similar to that.

Can someone please tell me where I can find this package?  I have seen mentions on the web of people building on this source, but can't find where to download it from.

Thanks,
Brett.

---

### Post by covert on 2008-09-17
sasc-ng only needs the headers to compile. I have no source link only build. In my case it is..

build -> /usr/src/linux-headers-2.6.24-16-generic

Naturally your one will be different to match your kernel version.

---

