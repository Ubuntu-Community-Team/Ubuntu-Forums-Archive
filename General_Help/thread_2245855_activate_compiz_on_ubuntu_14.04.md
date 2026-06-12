---
title: "activate compiz on ubuntu 14.04"
date: 2014-09-26
forum: General Help
---

### Post by darklandspider on 2014-09-26
im trying to enable compiz on ubuntu 14.04
did this:
```

#apt-get install compizconfig-setting-manager compiz-plugin

```
and got it installed.
within compizconfig manager i enabled wobbly windows
but the windows doesnt wobble :(

where did i go wronge?
thanx 4 help

---

### Post by deadflowr on 2014-09-26
What are you running in the first place?
Default Ubuntu uses compiz by default, so it should already be running.

It is quite possible, though, that you do not have a graphics card capable of running full compiz w/effects.
```
/usr/lib/nux/unity_support_test -p
```
post the output from this.

---

