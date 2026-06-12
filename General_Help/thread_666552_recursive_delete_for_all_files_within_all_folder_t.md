---
title: "recursive delete for all files within all folder that match *.wav"
date: 2008-01-13
forum: General Help
---

### Post by mitchelljj on 2008-01-13
Hi,

I would like to do a recursive delete within all folders for all files that match *.wav

While within the directory that contains all the folders I tried "rm -rf *.wav"

but that did not seem to work.

Thanks,

John

---

### Post by heindsight on 2008-01-13
To delete all .wav files under your home directory (for example), you can do:
```
find ~ -name "*.wav" -exec rm \{\} \;
```

---

