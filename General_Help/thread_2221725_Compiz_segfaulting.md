---
title: "Compiz segfaulting"
date: 2014-05-03
forum: General Help
---

### Post by DigiAngel on 2014-05-03
Topic says it....usually when trying to do window spread.  Things were running fine, but now it's not pretty:

May  3 11:08:13 iMac kernel: [  186.106951] compiz[2000]: segfault at 48 ip 00007f862d889120 sp 00007fff0637d728 error 4 in libscale.so[7f862d878000+25000]
May  3 11:08:43 iMac kernel: [  215.488379] compiz[3181]: segfault at 48 ip 00007f8bad7ae9e0 sp 00007fffbd6625a8 error 4 in libscale.so[7f8bad79e000+25000]
May  3 11:19:01 iMac kernel: [  124.454959] compiz[2098]: segfault at 48 ip 00007f26ae45e9e0 sp 00007fff5c5d1648 error 4 in libscale.so[7f26ae44e000+25000]
May  3 11:19:53 iMac kernel: [  176.565566] compiz[3124]: segfault at 48 ip 00007f35b32df9e0 sp 00007fffab5c69f8 error 4 in libscale.so[7f35b32cf000+25000]
May  3 11:21:50 iMac kernel: [   66.218279] compiz[2002]: segfault at 7f861547a000 ip 00007f85f7603664 sp 00007fffda2a1998 error 4 in libunityshell.so[7f85f73f6000+53c000]

Any thoughts on how to troubleshoot this?  Thank you.

---

