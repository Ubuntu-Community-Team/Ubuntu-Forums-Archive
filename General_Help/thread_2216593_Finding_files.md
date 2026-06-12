---
title: "Finding files"
date: 2014-04-12
forum: General Help
---

### Post by Langstracht on 2014-04-12
I have a bunch of sub-folders which each contain an *.html file.

I need to, from the parent folder find each (.html) file which contains a 'text string'
.
There are endless command line expressions on the 'net which purport to perform this task (using find, or grep, or egrep) but I am unable to find one that works.

Why that is I have to say is a bit of a mystery.

However if anyone would be prepared to proffer a command I'd much appreciate it.

TIA.

---

### Post by andrew.46 on 2014-04-12
Something like this might work:

```

find . -iname '*.html' | xargs grep -li 'text string'

```

---

### Post by steeldriver on 2014-04-12
Well, it might help if you told us what the 'text string' is (in case there's something unusual about it - special characters perhaps?) and some of the things you've tried? Anyhow here are some other things you can try

Simplest - will find instances of 'text string' in any non-binary files (regardless of extension):
```
grep -Ilr 'text string' /path/to/parent/
```

Old school (find files with .htm / .html extension (case insensitive) and grep for 'text string' in each non-binary one):
```
find tests -iname '*.htm?' -exec grep -Il 'text string' {} +
```

Using a recursive shell glob
```

shopt -s globstar

grep -Il 'text string' /path/to/parent/**/*.htm?

```

Add a lower-case -i to the greps if you want the actual 'text string' match to be case-insensitive.

---

### Post by Langstracht on 2014-04-13
```
find . -iname '*.html' | xargs grep -li 'text string'
```

worked just fine.  Thanks so much.

---

### Post by andrew.46 on 2014-04-13
> **Langstracht said:**
> worked just fine.  Thanks so much.

My pleasure :).

---

