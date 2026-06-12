---
title: "rdiffweb stopped working since updating to 24.04"
date: 2024-11-06
forum: General Help
---

### Post by freeflyjohn on 2024-11-06
I had rdiffweb installed and working on Ubuntu 20.04.

I have since upgraded to Ubuntu 24.04, but when I go to the rdiffweb URL ([http://localhost:8080/](http://localhost:8080/)) it says unable to connect.

Is it because Ubuntu 20.04 is not supported ?

It does say on the rdiffweb website...

[INDENT]The following Ubuntu Release are supported: Jammy (22.04), Kinetic (22.10), Lunar (23.04), Mantic (23.10)
[/INDENT]

Does anyone else use rdiffweb and have it working with Ubuntu 24.04 ?

---

### Post by 1fallen on 2024-11-06
Yep it's broken on Noble:
```
Unsatisfied dependencies:
 rdiffweb : Depends: python3-sqlalchemy (< 2) but 2.0.32+ds1-1ubuntu1 is to be installed
```

EDIT I did get it to work though rather hackish. PM me if your interested. I won't show this in the public eye.
This still works at this time on Plucky as well 25.04

EDIT This was resolved via a PM

---

