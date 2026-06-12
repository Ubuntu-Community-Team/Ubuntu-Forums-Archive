---
title: "Terminal - df -H | sort -k (can't figure out)"
date: 2017-10-21
forum: General Help
---

### Post by sprinterdriver on 2017-10-21
Hi.

I want to list all partitions using df -h command and then sort it by the percent coloumn.
From the output of df -H command alone, I found that the characters position for the first number of percent (character "1") - is 34 (by paste terminal output of df -H to Geany)

So the full command should be:
```
df -H | sort -k 34
```

The problem I run into, is that the _sort order is not what I expected_.
I've also tried to replace 34 by 33 and 35 - just to test if the character position count was wrong - but It still return a sort order that just don't make sense to me.

I have found some sources on the sort command at web that uses two numbers instead of a single number for coloumn sort - but it is hard to read the explanation so that it make sense - I assume that If I have wrote _sort -k 34.36 _ - then sort command wouldn't care about characters in position after 36 - not sure If I have make a correct assumption.

I have also came across web sites that have sort command examples that uses more than one occurrence of -k argument. Her I just guessing - does that mean that Sort command support sorting multiple columns in same command? (Never mind this question - the first problem must be solved first).

---

### Post by steeldriver on 2017-10-21
The `sort` command works on whitespace delimited *fields*, not characters (although you can specify a character *within *a field using a syntax like -k F.C)

So you probably want to sort on the 5th field - but numerically rather than lexically:

```

df -H | sort -nk 5

```

---

### Post by sprinterdriver on 2017-10-21
Thanks - that was excaclty what I wanted to know. That example above worked as I wanted :D

---

