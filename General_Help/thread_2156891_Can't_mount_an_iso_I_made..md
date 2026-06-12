---
title: "Can't mount an iso I made."
date: 2013-06-23
forum: General Help
---

### Post by Ashboy on 2013-06-23
I'm using x=Xubuntu 12.04. I have some old .bin files that I need to mount as CD's. I converted them to .iso's using:
```

(sudo apt-get install bchunk)
bchunk image.bin image.cue image.iso
```

That worked fine. Next I tried to mount them by right clicking on them and selecting "Archive Mounter", but nothing happens. No CD icon appears on the desktop, no CD device gets added in the file manager. This has never been a problem before with .iso's, but then this is the first time I tried making them myself. Does anyone know what might have gone wrong?

---

### Post by zero2xiii on 2013-06-23
Hay,

Give furius iso mount a go:
```
sudo apt-get install furiusisomount
```

And try both fuse and loop settings.

Cheers

---

### Post by Ashboy on 2013-06-23
Thanks. Cool program, didn't even need to convert to .iso with it. It just read the .bin.

---

