---
title: "What does the sort command with the -b option do?"
date: 2017-05-22
forum: General Help
---

### Post by John_Patrick_Mason on 2017-05-22
I can't seem to figure out what the -b option is for. I created 3 separate files with the following contents:
file1.txt:
(space)(space)y
(space)i
a
(space)(space)(space)h
file2.txt:
(space)p
r
(space)(space)(space)q
(space)(space)z
file3.txt:
(space)(space)(space)(space)n
c
(space)(space)f
(space)(space)(space)r
I then typed:
```
 sort -b file*.txt 
```
What I don't get is why I get the exact same output when I type:
```
 sort file*.txt 
```
then when I type the above command.

---

### Post by steeldriver on 2017-05-22
I think it just means that in your current locale, the space character sorts before any alphabetic characters - hence you can have as may leading spaces as you like with out altering the comparison.

```

$ diff -y <(sort -b file*.txt) <(sort file*.txt)
a                                                               a
c                                                               c
  f                                                               f
   h                                                               h
 i                                                               i
    n                                                               n
 p                                                               p
   q                                                               q
r                                                               r
   r                                                               r
  y                                                               y
  z                                                               z

```

That won't be the case in all locales - in the C locale for example:

```

$ diff -y <(LC_COLLATE=C sort -b file*.txt) <(LC_COLLATE=C sort file*.txt)
a                                                             <
c                                                             <
  f                                                           <
   h                                                          <
 i                                                            <
    n                                                               n
 p                                                            |    h
   q                                                               q
   r                                                               r
r                                                             |   f
  y                                                               y
  z                                                               z
                                                              >  i
                                                              >  p
                                                              > a
                                                              > c
                                                              > r

```

---

### Post by sisco311 on 2017-05-22
The locale specified by the environment affects the sort order. ;)

If you set LC_ALL or LC_COLLATE to C or POSIX you will see the differences:
```
LC_COLLATE=POSIX sort file*
LC_COLLATE=POSIX sort -b file*
```

EDIT: steeldriver beat me to it!

---

### Post by John_Patrick_Mason on 2017-05-22
> **sisco311 said:**
> The locale specified by the environment affects the sort order. ;)

If you set LC_ALL or LC_COLLATE to C or POSIX you will see the differences:
```
LC_COLLATE=POSIX sort file*
LC_COLLATE=POSIX sort -b file*
```

EDIT: steeldriver beat me to it!

OK, so I did:
```
LC_COLLATE=POSIX sort file*
```

which gave me the same as:
```
sort file*
```

which I then compared to:
```
LC_COLLATE=POSIX sort -b file*
```

which gave me an entirely different result.

The book I'm learning from says that:

> 
By default, sorting is performed on the entire line, starting with the first character in the line. [The -b option] causes sort to ignore leading spaces in lines and calculates sorting based on the first non-whitespace character on the line.


Now, correct me if I'm wrong, but if leading whitespaces are taken into account when using the sort command, and I'm still using Ubuntu's default locale, doesn't that mean that whitespaces under Ubuntu's default configuration come *after* the alphabetical characters? Also, doesn't that also mean that whitespaces come before the alphabetical characters when I decide to use POSIX as the locale?

---

### Post by John_Patrick_Mason on 2017-05-23
Bump

---

### Post by sisco311 on 2017-05-24
The collation rules used by each locale are stored in the /usr/share/i18n/locales/ directory. The one used by the POSIX locale is very simple. The order is the same as in the ASCII code set.

So yes, the space (ASCII 32) comes before the alphabetical characters (ASCII 65-90 97-122).

Other locales use more complex rules. Most of them are based on the ISO 14651 standard defined in the iso14651_t1 and iso14651_t1_common files. In this case, I think, whitespaces and punctuation marks are simply ignored.

HTH

---

### Post by John_Patrick_Mason on 2017-05-24
Thanks, sisco311. You just answered my question. Solved.

---

