---
title: "Case insensitive file name comparisons on FAT32"
date: 2007-10-10
forum: General Help
---

### Post by electronpusher on 2007-10-10
Unfortunately I have to do some binary comparisons of multiple files in directories on a FAT32 file system and a Linux system. Will diff work? Can I get diff  to compare files but disregard the case of the file names? When the files were copied from Linux to FAT32 file names lost case distinctions- I assume diff will report them as missing in the FAT32 partition. What can I do about this? Are there other programs that will disregard case in file names? Thanks  for any assistance any one can give.

---

### Post by pointone on 2007-10-10
man is probably the most useful command in Linux.

```
man diff
```

... tells us that the --ignore-file-name-case option will ignore case when comparing file names with diff.

---

### Post by electronpusher on 2007-10-11
Sorry about the dumb question... I checked it myself a little later and I'm all set! I guess I was in a hurry and a little frazzled. Double Thanks!

---

