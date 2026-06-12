---
title: "[SOLVED] How can i create a cue file for a bin"
date: 2008-06-10
forum: General Help
---

### Post by afbase on 2008-06-10
Would anyone know if there is a way to create a cue file for a bin file?

---

### Post by sizzam on 2008-06-10
Assuming the name of your bin file is 'filename.bin',  create a text file in the same directory as the bin called 'filename.cue'.

The contents of 'filename.cue' should look like this:
```
FILE &#8220;filename.bin&#8221; BINARY
TRACK 01 MODE1/2352
INDEX 01 00:00:00
```

That should be all you need to be able to burn it.

---

