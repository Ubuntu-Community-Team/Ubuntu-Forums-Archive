---
title: "transcode / ripmake not sync sound and movie"
date: 2008-04-29
forum: General Help
---

### Post by soxs on 2008-04-29
ripmake/transcode shifts the sound line always 0,5 from the actual film. But it only happens when decoding the whole DVD. The example is just ok.
Maybe someone point me where my failure lies burried, or how to fix ths timeshift.
The comand which I use to make my ripmake file is:
```
ripmake -n pal -c 1 -C 4599 -g 720,560 /dev/hda ogm
```
```
make -f ./hda-ogm.mak
``` syncs sound and picture just right
whereas ```
make -f ./hda-ogm.mak rip
``` loses sync (~0,5s delay)

Note: This is not an illegal action.

---

### Post by soxs on 2008-04-30
no one?
Bump -.-

---

