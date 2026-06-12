---
title: "lighttpd problem"
date: 2007-03-11
forum: General Help
---

### Post by I.You on 2007-03-11
Hello.

I installed pcre and lighttpd in different directories other than
default :

#./configure --prefex=/modules/test/ --libdir=/modules/lib

and running :

can't handle '$HTTP(url) =~ ...' as you compiled without pcre support.
(perhaps just a missing pcre-devel package ?)
2007-03-07 05:06:20: (configfile.c.827) source: dev/lighttpd.conf line:
67 pos: 2 parser failed somehow near here: {

this error is because lighttpd can't recognize the pcre lib.
is there anyone who know this?

help me please.

---

