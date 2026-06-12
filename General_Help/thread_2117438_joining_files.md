---
title: "joining files"
date: 2013-02-18
forum: General Help
---

### Post by dwlamb on 2013-02-18
I have some large files that were split with a simple splitter program in DOS but I want to rejoin the segments in Linux. 

What is the corresponding syntax for joining files at the command-line comparable to ```
copy/b file1+file2+file3 bigfile
``` in a Windows/DOS environment? Can it be done with cat at the command line?

---

### Post by codemaniac on 2013-02-18
```
cat file1 file2 file3 > bigfile
```

or 

```
cat file[1-3] > bigfile
```

---

