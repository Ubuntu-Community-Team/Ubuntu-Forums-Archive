---
title: "Maxima locks up"
date: 2006-09-02
forum: General Help
---

### Post by Abild on 2006-09-02
Hi all,

I have a problem with Maxima

It locks up every time i tries to calculate something.
```

Maxima 5.9.3.99rc2 http://maxima.sourceforge.net
Using Lisp CMU Common Lisp CVS release-19a 19a-release-20040728 + minimal debian patches
Distributed under the GNU Public License. See the file COPYING.
Dedicated to the memory of William Schelter.
This is a development version of Maxima. The function bug_report()
provides bug reporting information.
(%i1) 1+1


```

After this it locks up until i press Ctrl+C:

```

Maxima encountered a Lisp error:

 Interrupted at #xFFFFE410.

Automatically continuing.
To reenable the Lisp debugger set *debugger-hook* to nil.
(%i1) 

```

I have recompiled maxima according to theese instructions but without luck. [https://help.ubuntu.com/community/wxMaxima](https://help.ubuntu.com/community/wxMaxima)

I really need maxima for schoolwork.
Thanks in advance :)

---

### Post by gborzi on 2006-09-02
You need to put a semicolon ( ; ) in order to obtain the result, e.g.
> Maxima 5.9.2 [http://maxima.sourceforge.net](http://maxima.sourceforge.net)
Using Lisp CMU Common Lisp CVS release-19a 19a-release-20040728 + minimal debian patches
Distributed under the GNU Public License. See the file COPYING.
Dedicated to the memory of William Schelter.
This is a development version of Maxima. The function bug_report()
provides bug reporting information.
(%i1) 1+1;

(%o1)                                  2
(%i2)

---

### Post by Abild on 2006-09-02
Ahh, Thanks alot :)

I knew this really. I guess summer holliday makes you forget lots of stuff :)

---

