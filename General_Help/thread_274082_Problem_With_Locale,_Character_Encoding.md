---
title: "Problem With Locale, Character Encoding"
date: 2006-10-09
forum: General Help
---

### Post by tmountain on 2006-10-09
Hi. I've installed Ubuntu Dapper Drake LTS on a few servers, and I'm having this problem across the board. When using pstree and a few other commands, the output is littered with `ââ' characters. Here's an example:

initââ¬âatd
     ââcronâââcronâââshââârun-partsâââman-dbâââmandb
     ââdd
     ââevents/0
     ââ6*[getty]
     ââkhelper
     ââkjournald
     ââklogd
     ââksoftirqd/0
     ââkswapd0

I've searched this forum and google, but nothing I've tried so far has worked. I found this thread and tried all the solutions suggested.

[http://linux.derkeiler.com/Mailing-Lists/Debian/2006-08/msg01370.html](http://linux.derkeiler.com/Mailing-Lists/Debian/2006-08/msg01370.html)

Any help would really be appreciated because this issue is pretty annoying.

---

### Post by Average Joe on 2006-10-09
Have you tried to set the character encoding of the terminal to some UTF-8 type? In the menubar of the terminal you can go to Terminal > Set Character Encoding > Add and Remove to change it.

Mine is set to Current Locale (UTF-8 ), and my locale is set to en_US.UTF-8. But when I change the terminal character encoding to e.g. Western (Windows-1252), I get similar strange output for pstree as you do now.

Hope this helps.

---

### Post by tmountain on 2006-11-09
That solved it. Thanks very much!

---

