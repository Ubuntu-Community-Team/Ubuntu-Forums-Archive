---
title: "Live-Build won't build an iso image"
date: 2017-12-07
forum: General Help
---

### Post by thelinuxbox on 2017-12-07
Hello everyone, I'm a bit stuck, I'm trying to build a basic ubuntu minimal iso (for fun) using live-build, for  some reason the process won't build the iso image,  I've also tried adding quotation marks around iso-hybrid but this makes no difference to the end result, no iso is created, please could someone explain where I am going wrong, I've been researching since last week  trying to build the ISO but haven't had much luck, any feedback is gratefully appreciated, thank you very much :)

```
#!/bin/sh

sudo lb clean

sudo lb config \
 --mode ubuntu \
 --architecture amd64 \
 --distribution xenial \
 --archive-areas "main universe multiverse" \
 --parent-distribution xenial \
 --parent-archive-areas "main universe multiverse" \
 --apt-options "--yes" \
 --binary-images iso-hybrid

sudo lb build
```

---

### Post by thelinuxbox on 2017-12-13
Hi, any feedback would be much appreciated, thank you very much.

---

