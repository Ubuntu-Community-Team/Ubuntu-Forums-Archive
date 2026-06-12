---
title: "merge lines text file"
date: 2008-04-14
forum: General Help
---

### Post by p.becks on 2008-04-14
Hello,

I have 2 files which look like this:

<file1.txt>

ESSID1 
ESSID2 
ESSID3 

<file2.txt>

ON
OFF
ON

Now i want to merge them from the command line so they look like this:

ESSID1 ON
ESSID2 OFF
ESSID3 ON

how????

---

### Post by ghostdog74 on 2008-04-14
```

# paste file1 file2
ESSID1  ON
ESSID2  OFF
ESSID3  ON


```

---

### Post by p.becks on 2008-04-15
thnx!

---

