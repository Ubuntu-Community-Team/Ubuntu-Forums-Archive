---
title: "Need help using grep"
date: 2013-01-31
forum: General Help
---

### Post by nativehound on 2013-01-31
I need help greping a log. I want to pull the last line containing the word “project” in my Folding@Home log and output it to my conky.


```
cat FAHlog.txt | grep Project

[08:39:28] Project: 8072 (Run 0, Clone 284, Gen 48)
[19:31:37] Project: 8072 (Run 0, Clone 284, Gen 48)
[01:46:05] Project: 8072 (Run 0, Clone 284, Gen 48)
[05:47:48] Project: 8072 (Run 0, Clone 284, Ge
[COLOR="DarkRed"][05:47:50] Project: 7660 (Run 253, Clone 0, Gen 18)[/COLOR]
```


How do I isolate just the last entry for “project” using grep?

---

### Post by steeldriver on 2013-01-31
pipe it through 'tail -1'? also you don't need the 'cat' e.g.

```
grep 'Project' FAHlog.txt | tail -1
```

---

### Post by nativehound on 2013-01-31
WooHoo,TY steeldriver. That was fast.

---

### Post by steeldriver on 2013-01-31
You're welcome - there may be a more elegant way of course 

'grep' *does* allow you to stop after the mth match so I guess you could cat it backwards and find the *first* match

```
 tac FAHlog.txt | grep -m1 'Project'
```

but I doubt it's more efficient. Also the 'cat haters' will probably er.. have kittens at 'tac' ;)

---

### Post by raja.genupula on 2013-01-31
please mark your thread as solved .

---

### Post by codemaniac on 2013-01-31
An awk solution below, however steeldriver's solution is easier to the eyes. ;)

```
awk '/Project/{} END{print}' FAHlog.txt
```

---

### Post by Vaphell on 2013-01-31
> ```
awk '/Project/{} END{print}' FAHlog.txt
```
that doesn't work
```
$ echo $'a1\nb\na2\nc' | awk '/a/{} END{ print; }'
c
$ echo $'a1\nb\na2\nc' | awk '/a/{ x=$0; } END{ print x; }'
a2
```

---

### Post by codemaniac on 2013-01-31
thanks for the fix vaphell :), i can see it the bug.

---

### Post by darkager on 2013-02-01
I know this is marked solved, but thanks guys.  As someone new to linux (but familiar with piping via Powershell), this is the kind of stuff that helps me the most.

---

