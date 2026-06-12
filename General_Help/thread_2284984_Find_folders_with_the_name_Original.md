---
title: "Find folders with the name Original"
date: 2015-07-02
forum: General Help
---

### Post by alfirdaous on 2015-07-02
Hello everybody,

I would like to find folders in current directory with the name "Original" and larger than 50M

```
find -iname *Original* -type d -size +50M -exec du -h {} \; | sort -n

```

This command line returns empty 

Thanks in advance

---

### Post by steeldriver on 2015-07-02
Probably the issue is combining '-size' with '-type d'

A directory's size is not the size of files contained in it - just the size of the inode metadata (likely only a few kB) - so won't meet your -size +50M test

As a side note, always quote globs like "*Original*" or '*Original*' in arguments like this - else they may get expanded by the shell before being passed to `find`

---

### Post by aromo2 on 2015-07-02
This one works as expected:
```
find . -name "*Original*" -type d -exec du -m {} \; | awk '{ if ( $1 > 50 ) {print $0} }' | sort -n
```

Give it a try.

---

### Post by alfirdaous on 2015-07-03
Thanks aromo2, it works perfect

---

