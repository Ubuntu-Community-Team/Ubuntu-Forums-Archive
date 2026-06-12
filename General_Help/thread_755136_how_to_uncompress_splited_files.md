---
title: "how to uncompress splited files"
date: 2008-04-14
forum: General Help
---

### Post by karq on 2008-04-14
So how to uncompress splited files? I have a 4,7gb iso, what is splited into many parts. I tried the achive manager, but its just uncompress'es and never finishes.

---

### Post by sisco311 on 2008-04-14
use the cat command to concatenate the files
```
cat file.iso1 file.iso2 file.iso3 .. > file.iso
```

---

### Post by karq on 2008-04-14
That iso is in splited rar files :D

---

### Post by bodhi.zazen on 2008-04-14
> **sisco311 said:**
> use the cat command to concatenate the files
```
cat file.iso1 file.iso2 file.iso3 .. > file.iso
```

Yes, I advise >>

two >> ( a single > = over write ; >> = add to)

Also I advise you use a unique name for the output file (or you will overwrite the first piece)

```
cat file_part1.iso1 file_part2.iso2 file_part3.iso3 .. >> full_file.iso
```

---

### Post by sisco311 on 2008-04-14
first install the unrar package:
```
sudo aptitude install unrar
```or [click here if you are using Ubuntu 7.10 (Gusty Gibbon)]("apt:unrar")
 
then try to extract it with archive manager.

---

### Post by karq on 2008-05-02
Thanks a lot for help.

---

