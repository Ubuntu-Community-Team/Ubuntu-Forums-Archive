---
title: "grep assistance"
date: 2007-04-02
forum: General Help
---

### Post by jazzor on 2007-04-02
How do I use grep to match a strict pattern eg I have:
124
1
235
456
1abc
a1bc
1-abc
1
ab 1 c

and I want to grep just the line(s) containing strictly "1".
grep <script> output:
1
1

If I do grep "1" I get:
123
1
1abc
a1bc
1-abc
1
ab 1 c

which is not what I want.
and if I do grep -w "1" I get:
1
1-abc
1
ab 1 c

which is not what I want either.

---

### Post by justleen on 2007-04-02
Both of the following commands print all lines matching exactly "abc" or "def" :

grep -E '^abc$|^def$'

grep -F -x 'abc
def'

---

