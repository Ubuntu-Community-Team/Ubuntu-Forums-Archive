---
title: "collapsing redundant path i.e. &quot;/./&quot;"
date: 2012-11-14
forum: General Help
---

### Post by hwttdz on 2012-11-14
There are many ways of expressing a single path in linux, for instance:
/usr/local/bin
is the same location as
/usr/local/./bin
or 
/usr/local/../local/bin
and ....
Is there a simple way of getting what you might think of as the canonical path to a file given a path to the file?  I'm not quite sure what I mean, but my first thought is that I mean the path which contains the fewest slashes.

---

### Post by dannyboy79 on 2012-11-14
> **hwttdz said:**
> I'm not quite sure what I mean, but my first thought is that I mean the path which contains the fewest slashes.
if you don't know what you mean, we won't. LOL  I am not sure what you're asking but the least amount of slashes is obviously
/usr/local/bin/

---

### Post by sisco311 on 2012-11-14
You can use the realpath command to print the resolved absolute file name:
```
realpath *file*
```
For more details, check out:
```

man realpath
info coreutils 'realpath invocation'

```

---

