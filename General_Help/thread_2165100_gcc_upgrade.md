---
title: "gcc upgrade"
date: 2013-08-03
forum: General Help
---

### Post by icegood on 2013-08-03
I have same issue as [there]("http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=707957") i.e. cannot  compile anything with -m32
How properly can i upgrade gcc if there is no such in my repositories?


```

uname -a
Linux ubuntu 3.8.0-27-generic #40-Ubuntu SMP Tue Jul 9 00:17:05 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux



```

---

### Post by icegood on 2013-08-04
Everything at least in "raring" is OK.
[COLOR=#333333][FONT=Ubuntu Mono]apt-get install lib32stdc+[/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu Mono]+6-4.7-[/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu Mono]dev[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu Mono]solves the problem.[/FONT][/COLOR]

---

