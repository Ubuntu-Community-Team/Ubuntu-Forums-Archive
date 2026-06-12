---
title: "how to grep for 3 empty lines together"
date: 2018-05-20
forum: General Help
---

### Post by Skaperen on 2018-05-20
a bunch of files (of a lot more files in the same subdirectory) have 3 empty lines in sequence at some point in the file.  all other empty lines are alone.  i would like to get a list of which files have the 3 empty lines together.  i tried _egrep -l '$$$' *_ and _egrep -l '^$^$^$' *_ but they both listed all the files there.  so that must be the wrong regular expression.  **anyone know the right way to do it?**

---

### Post by kerry_s on 2018-05-21
```
grep -E "   " some.txt
```

---

### Post by spjackson on 2018-05-21
```

grep -zlP '^\n\n\n' *

```

---

### Post by kerry_s on 2018-05-21
> **spjackson said:**
> ```

grep -zlP '^\n\n\n' *

```

my bag i was thinking spaces. :o

---

### Post by Skaperen on 2018-05-23
the -P option (for PCRE) always gives me the error message "grep: conflicting matchers specified" in that combination and all alternatives i tried.  i coded a Python script to do what i needed.

---

### Post by spjackson on 2018-05-24
> **Skaperen said:**
> the -P option (for PCRE) always gives me the error message "grep: conflicting matchers specified" in that combination and all alternatives i tried.  i coded a Python script to do what i needed.
Did you use grep or egrep? I notice you were using egrep in your original post.
```

egrep -P
grep: conflicting matchers specified

```
The code I gave works correctly with GNU grep 2.20 but not with GNU grep 2.25 (and presumably above) which complains about the ^.
```

grep -zlP '\n\n\n' *
```
is insufficient because the first newline matches one at the end of a non-empty line.
```

grep -zlP '\n\n\n\n' *
```
would in general work but miss files where the first 3 lines are blank.

 As you've solved your problem I won't pursue it further.

---

### Post by Skaperen on 2018-05-24
i did use _[FONT=courier new]egrep[/FONT]_.  i've always believed that _[FONT=courier new]grep[/FONT]_ would be the same as either _[FONT=courier new]egrep[/FONT]_ or _[FONT=courier new]fgrep[/FONT]_ depending on how it is configured.  so i learned a new thing today.

"Any day i don't learn something is a wasted day" --Skaperen

but i will go test this (i still have the original files and can make some hardlinks in a temp directory) anyway, out of curuosity.

got:  [COLOR=#ff0000][FONT=courier new]grep: unescaped ^ or $ not supported with -Pz[/FONT][/COLOR]

oh well...

and i have never understood classic regular expressions or PCRE.  all "string" programming i have done was in C without using any libraries other than my own.  i could always figure out a procedural way to do these things.   now i am using Python so i am sure this will change over time.

---

