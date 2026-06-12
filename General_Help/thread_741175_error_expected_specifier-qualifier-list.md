---
title: "error: expected specifier-qualifier-list"
date: 2008-03-31
forum: General Help
---

### Post by lewang on 2008-03-31
Hello,

I am trying to compile iwlist.c iwlib.h wireless.h retrieved from wireless-tools_29~pre20.orig.tar.gz using the command: gcc -Wall iwlist.c iwlib.h wireless.h -o iwinfo, but there are some errors as the following,
--------------------------------------------------------------------
wireless.h:540: error: expected specifier-qualifier-list before ‘__s32’
wireless.h:552: error: expected ‘:’, ‘,’, ‘;’, ‘}’ or ‘__attribute__’ before ‘*’ token
wireless.h:567: error: expected specifier-qualifier-list before ‘__s32’
wireless.h:578: error: expected specifier-qualifier-list before ‘__u8’
wireless.h:594: error: expected specifier-qualifier-list before ‘__u32’
wireless.h:607: error: expected specifier-qualifier-list before ‘__u32’
wireless.h:615: error: field ‘addr’ has incomplete type
wireless.h:634: error: expected specifier-qualifier-list before ‘__u8’
wireless.h:696: error: expected specifier-qualifier-list before ‘__u32’
wireless.h:710: error: expected specifier-qualifier-list before ‘__u16’
wireless.h:724: error: expected specifier-qualifier-list before ‘__u32’
wireless.h:732: error: expected specifier-qualifier-list before ‘__u32’
wireless.h:741: error: expected specifier-qualifier-list before ‘__u32’
wireless.h:753: error: expected specifier-qualifier-list before ‘__u16’
wireless.h:776: error: ‘IFNAMSIZ’ undeclared here (not in a function)
wireless.h:791: error: expected specifier-qualifier-list before ‘__u32’
wireless.h:835: error: expected specifier-qualifier-list before ‘__u32’
wireless.h:947: error: expected specifier-qualifier-list before ‘__u32’
wireless.h:965: error: expected specifier-qualifier-list before ‘__u16’
--------------------------------------------------------------------
How can I fix this? Thanks for your any idea in advance.

BR,
Leon

---

