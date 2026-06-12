---
title: "more on locales (exporting LANG)"
date: 2004-12-11
forum: General Help
---

### Post by burlap on 2004-12-11
I know this questions is coming back, but still does not have a definitive answer:

I have configured (with "dpkg-reconfigure locales") three different locales for my system (although I have tried different configurations let's focus on this one):

```
$locale -a
C
en_US
en_US.iso88591
es_ES
es_ES.iso88591
pl_PL
pl_PL.iso88592
polish
POSIX
spanish

```
Polish is default. However, sometimes I need to run programs in Spanish or English. I used to do it by:

```
$LANG=es_ES foo
```

It doesn't work anymore. I can only get English with

```
$LANG=C foo or 
$LANG=posix foo
```

I do not consider this to be a solution, because 

```
$LANG=en_US foo
```

doesn't work.

How to use LANG in Ubuntu?

---

