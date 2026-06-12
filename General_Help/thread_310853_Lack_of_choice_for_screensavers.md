---
title: "Lack of choice for screensavers?"
date: 2006-12-01
forum: General Help
---

### Post by some.hacker on 2006-12-01
I recently installed edubuntu 6.10 edgy and found that the available number of screensavers is down from about a jillion in dapper to 3 in edgy. Is there a place I can install all the screensavers that came with dapper? Is there a screensaver pack for gnomescreensaver somewhere I can download? 

Thanks for helping.

---

### Post by 23meg on 2006-12-01
Screensavers are in the following packages: xscreensaver-data, xscreensaver-gl, xscreensaver-data-extra, xscreensaver-gl-extra .

Easy way to find things like this yourself:
```
$ apt-cache search screensaver
```
or
```
$ apt-cache search --names-only screensaver
```

---

