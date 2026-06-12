---
title: "Weird libxslt - libxml error"
date: 2012-11-27
forum: General Help
---

### Post by morningsunshine on 2012-11-27
I am using ubuntu lucid x64. This is a new install on my test VM. I installed a custom package given by the sys admin guys. This package is already running on other servers perfectly fine. When I try to use a functionality in this application, I get this error message:

ImportError: /usr/lib/libexslt.so.0: symbol xsltInitGlobals, version LIBXML2_1.1.25 not defined in file libxslt.so.1 with link time reference

> root@localhost:lib# ll libxslt*
-rw-r--r-- 1 root root 397636 2012-09-29 02:04 libxslt.a
-rw-r--r-- 1 root root    955 2012-09-29 02:04 libxslt.la
lrwxrwxrwx 1 root root     17 2012-11-28 01:01 libxslt.so -> libxslt.so.1.1.26
lrwxrwxrwx 1 root root     17 2012-11-28 01:01 libxslt.so.1 -> libxslt.so.1.1.26
-rw-r--r-- 1 root root 241576 2012-09-29 02:04 libxslt.so.1.1.26

> 
root@localhost:lib# ll libxml*
-rw-r--r-- 1 root root 2126758 2012-09-26 23:41 libxml2.a
-rw-r--r-- 1 root root     929 2012-09-26 23:41 libxml2.la
lrwxrwxrwx 1 root root      16 2012-11-28 00:57 libxml2.so -> libxml2.so.2.7.6
lrwxrwxrwx 1 root root      16 2012-11-28 00:57 libxml2.so.2 -> libxml2.so.2.7.6
-rw-r--r-- 1 root root 1372344 2012-09-26 23:41 libxml2.so.2.7.6

I couldn't find any similar issue anywhere including these forums, so posting now. Any pointers will be helpful.

Many Thanks.

---

