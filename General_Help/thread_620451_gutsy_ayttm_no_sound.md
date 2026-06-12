---
title: "gutsy: ayttm no sound"
date: 2007-11-22
forum: General Help
---

### Post by Georges on 2007-11-22
ayttm has no sound.

I get the following error: 
```

sound.c[263]:play_esd_file - Ayttm: Esd play file failed with code 0

```

I tried ayttm from debian unstable, same problem

then from etch:
sudo dpkg -i --force-depends-version ayttm_0.4.6+34-3_i386.deb

ok, some stuff does not work (dependencies missing) but **in that version the sound is actually working**!

So what's going on????

Georges

---

