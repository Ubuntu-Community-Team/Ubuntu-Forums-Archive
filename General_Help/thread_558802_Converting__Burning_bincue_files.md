---
title: "Converting / Burning bin/cue files"
date: 2007-09-24
forum: General Help
---

### Post by jon_gunnar on 2007-09-24
I have two files, bin and a cue file.
bchunk will not convert,saying the size is to big:

```
bchunk doksdvd.bin doksdvd.cue doks.iso
```

Gives:

```
Could not open BIN doksdvd.bin: File too large
```

The file is is around 3.7Gb. k3b will not burn dvd size cue files as far as I can see.

Is it possible to do this at all?

---

### Post by energiya on 2007-09-24
use [cdemu](http://cdemu.org/) to mount or [bin2iso](http://mange.dynalias.org/linux/bin2iso/), [bchunk](http://he.fi/bchunk/) to convert to ISO.

---

### Post by felixnine on 2007-11-05
i'm also having this problem; i have a dvd image in bin/cue format. bin2iso creates a zero-length iso and bchunk generates some weird files that aren't isos. how on earth do you do this?

---

### Post by energiya on 2007-11-06
There is also [PowerISO](http://www.poweriso.com/download.htm). The linux version is free ;)

---

