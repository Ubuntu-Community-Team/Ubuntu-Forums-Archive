---
title: "Firefox 1.0.7 locks up every so often"
date: 2005-10-20
forum: General Help
---

### Post by reuben on 2005-10-20
I have noticed a significant decrease in stability over the past couple of versions of firefox. Has anybody else noticed similar?

It seems to lock up, inconsistently, on javascript calls. The only thing I can do is terminate the process, and then restart.

---

### Post by rmjokers on 2005-10-20
I have had it freeze 3 or 4 times in the past few months when I try to do a Ctrl-F search in a web page.  This may be a different problem than what you are noticing though.

---

### Post by mykey on 2005-10-20
try to run it without pango and watch if it does it too
**sudo gedit /usr/bin/firefox**
and find
```
MOZ_ENABLE_PANGO=1
export MOZ_ENABLE_PANGO
```
then put a # in front of each of those lines - restart firefox

---

### Post by reuben on 2005-10-20
Yeah, that seems to have done the trick. (Seems)

Is this a known issue? Should I report it?

---

### Post by mykey on 2005-10-20
I don't think so - the developers seem to be eager to make firefox use pango - I found it to run more slick and responsive without that integration - but I am sure they're working on it. ;)

---

