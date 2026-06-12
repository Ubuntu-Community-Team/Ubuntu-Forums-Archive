---
title: "[SOLVED] How to write sums of data in bash script?"
date: 2008-04-17
forum: General Help
---

### Post by abcuser on 2008-04-17
Hi,
using Ubuntu 7.10 Desktop I would like to write bash skript to get some sums.

My file looks like this:
```

A
A
A
B
B
C
D

```

I would like to get sums of A, B, etc. So output should be:
```

A 3
B 2
C 1
D 1

```

How to write such a script?
Thanks,
Abcuser

---

### Post by abcuser on 2008-04-17
Hi,
found out solution from web page:
[http://www.unix.com/shell-programming-scripting/51129-column-sum-group-uniq-records.html](http://www.unix.com/shell-programming-scripting/51129-column-sum-group-uniq-records.html)

awk '{arr[$1]+=$2} END {for (i in arr) {print i,arr[i]}}' input_file
Thanks,
Grofaty

---

### Post by marufaberlin on 2008-04-17
Does it need to be a bash script? Could it be a c program?

---

### Post by ghostdog74 on 2008-04-17
> **abcuser said:**
> Hi,
found out solution from web page:
[http://www.unix.com/shell-programming-scripting/51129-column-sum-group-uniq-records.html](http://www.unix.com/shell-programming-scripting/51129-column-sum-group-uniq-records.html)

awk '{arr[$1]+=$2} END {for (i in arr) {print i,arr[i]}}' input_file
Thanks,
Grofaty

are you sure you got what you want. ?
```

# awk '{a[$0]++}END{for (i in a)print i,a[i]}' file
A 3
B 2
C 1
D 1


```

---

### Post by Trail on 2008-04-17
How about
```

cat yourfilename | sort | uniq -c

```

"sort" obviously sorts the input, and "uniq -c" counts the unique occurences of the data found, and prints them with that number prepended before the data.

---

### Post by ghostdog74 on 2008-04-17
> **Trail said:**
> How about
```

cat yourfilename | sort | uniq -c

```

"sort" obviously sorts the input, and "uniq -c" counts the unique occurences of the data found, and prints them with that number prepended before the data.

1) no need for cat. sort file will do 
2) output is reversed
3) Slower if encounter large files, eg
```

 # head -10 file
A
A
A
B
B
C
D
A
A
A
# wc -l file
14486661 file
# time sort file | uniq -c
6208569 A
4139046 B
2069523 C
2069523 D

[COLOR="Red"]real    0m37.214s[/COLOR]
user    0m36.746s
sys     0m0.412s
# time awk '{a[$0]++}END{for (i in a)print i,a[i]}' file
A 6208569
B 4139046
C 2069523
D 2069523

[COLOR="Red"]real    0m7.651s[/COLOR]
user    0m7.492s
sys     0m0.032s
#                             


```

---

