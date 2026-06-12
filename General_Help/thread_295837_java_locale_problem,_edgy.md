---
title: "java locale problem, edgy"
date: 2006-11-08
forum: General Help
---

### Post by Booty on 2006-11-08
Hello, im experiencing such trouble with java-1.5.0-sun-1.5.0.08 on Edgy system.
Its locale problem. I tried running netbeans 5.5 and also 
few swing demos from java distribution. My native locale is russian unicode:
LANG=ru_RU.UTF-8 but  when im trying to type some text in russian into java app, text instead typed on arabian language in opposite direction :shock: 
I tried downloading and installing jdk-1.6 from sun site, but there things
was even worse.
I guess it is kinda problem with X11 locales. What do yo think ?

---

### Post by Booty on 2006-11-09
As additinon.
SWT java apps, like azureus, works just fine, the big problem only with
Swing thingie.

---

### Post by Booty on 2006-11-09
It seems i found solution, maybe it not very graceful, but it works.
when starting swing program i need first to change locale to en_US.UTF-8
and then have no problem with charsets.
Sorry if my english is awful :mrgreen:

---

