---
title: "need to batch zip a whole bunch of files each in seperate archives"
date: 2007-10-10
forum: General Help
---

### Post by __knk__ on 2007-10-10
basically as the name states, ive got a whole  bunch of roms for my psp and im wanting to compress them all to save some space, however i can only seem to compress them into one large archive.

i need them in seperate archives with the name being the same as filesname, theres 790(more to come) of them so individually is not an option:).  reason im doin this is coz the emulator supports zip compression and i save about 50% space on these.

thanks

---

### Post by nick_h on 2007-10-10
Is something like:
```
for f in *; do zip "$f" "$f"; done
```
what you want?

---

### Post by Old *ix Geek on 2007-10-10
Here you go:
```
for dir in `ls`
do zip $dir $dir/*
mv $dir*zip $dir
done
```

---

### Post by __knk__ on 2007-10-11
thanks guys worked i used nick_h's method with a slight modification as it didnt work:)

for f in *; do zip "$f.zip" "$f"; done

just added .zip.  thanks again:)

---

