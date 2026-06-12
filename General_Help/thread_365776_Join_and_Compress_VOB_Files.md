---
title: "Join and Compress VOB Files"
date: 2007-02-20
forum: General Help
---

### Post by JoshHendo on 2007-02-20
Hello All.

I have some vob files that I wish to combine into 1 file and then compress them (2 vob files that continue from where the last left off).

I was wondering if there is a program that will do that and keep the 16:9 (or whatever the ratio is) ratio.

I believe ffmpeg can compress VOB files, but I don't know how to join them.

Thanks!

- Josh

---

### Post by Jussi Kukkonen on 2007-02-20
vob should be a mpeg stream, so you could try the simple solution:
```
cat 1.vob 2.vob > 1and2.vob
```

---

### Post by orb9220 on 2007-02-20
I use dvdShrink thru wine. And just hit the reauthor button and add vob's I want. And can also  set start and end frames for each one and also adjust how much compression I want for each vob.

I find video editing very limited in linux unless you are a command line junkie.

---

