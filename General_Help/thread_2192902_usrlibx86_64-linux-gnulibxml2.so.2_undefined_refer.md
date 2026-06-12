---
title: "/usr/lib/x86_64-linux-gnu/libxml2.so.2: undefined reference to `gzopen64@ZLIB_1.2.3.3"
date: 2013-12-10
forum: General Help
---

### Post by sara.bolognesi on 2013-12-10
Hi,
I'm installing a "private" software (software developed from someone else) 
which I know for sure it works fine in other environments (eg, SLC6)
Trying to install it on Ubuntu 12.04, I get the following problem:
/usr/lib/x86_64-linux-gnu/libxml2.so.2: undefined reference to `gzopen64@ZLIB_1.2.3.3'

I installed libxm2-dev as well as zlib (I think the native version
with Ubuntu was 1.2.4. but I tried also to install an older one 1.2.3 
or the latest 1.2.8.). 
I also tried to install first zlib and afterward libxml2-dev and viceversa.

Looking around on the web for "libxml2.so.2: undefined reference to `gzopen64@ZLIB_1.2.3.3"
looks like a quite frequent problem but I couldn't find a solution anywhere...

Any help would be much appreciated, 
thanks!!!!!!!!!

sara

---

