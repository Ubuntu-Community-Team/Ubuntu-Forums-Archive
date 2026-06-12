---
title: "{shell scripting} Counting the number of occurrences of each letter in a text?"
date: 2013-04-16
forum: General Help
---

### Post by GnuKian on 2013-04-16
I need to measure the number of times each letter is used in a text. I know "wc" can print newline, word, and byte counts for each file, but I don't know how-to? (also it should support UTF8)

---

### Post by dcstar on 2013-04-16
Sort the whole thing in ascii order and count up the number of instances of each character.

```
man sort
man awk
```

Don't expect much more, people here are tired of doing people's school assignments for them.

---

### Post by prodigy_ on 2013-04-16
Is that homework? ;) Well, anyway (using python):
```
#!/usr/bin/env python

from collections import defaultdict

a_z = [chr(n) for n in xrange(97, 123)]

with open('/path/to/file', 'r') as file:
    chars = [char.lower() for char in file.read()]
    d = defaultdict(int)
    for c in chars:
        if c in a_z:
            d[c] += 1

print sorted(d.items())
```

---

### Post by cortman on 2013-04-16
Grep for the letter and pipe it to wc.

---

### Post by Lars Noodén on 2013-04-16
> **GnuKian said:**
> I need to measure the number of times each letter is used in a text. I know "wc" can print newline, word, and byte counts for each file, but I don't know how-to? (also it should support UTF8)

There are a lot of recipes on the net for perl, awk or most any other language.  The phrase to look for is "frequency count"

---

### Post by GnuKian on 2013-04-16
> **prodigy_ said:**
> Is that homework? ;) 
NO, be sure!
I'm going to determin the importance or applicability of any of the alphabet in my native language. 
Then I run the program on a variety of classic and modern literature and children's literature and also scientific ones.
I'll graph data and after some statistical work, I send the information to the National Institute of Standards. I hope they take action to change the current standard layout which is epraximately an alphabetical arrangement of letters and not a reproducibility arrangement based on ergonomic principles.

> **dcstar said:**
> Don't expect much more, people here are tired of doing people's school assignments for them.Oh! I did not look at the forum that way! I did not care to look at how you spend busy days, Sorry.

> 
Well, anyway (using python):
```
#!/usr/bin/env python

from collections import defaultdict

a_z = [chr(n) for n in xrange(97, 123)]

with open('/path/to/file', 'r') as file:
    chars = [char.lower() for char in file.read()]
    d = defaultdict(int)
    for c in chars:
        if c in a_z:
            d[c] += 1

print sorted(d.items())
```
It work for English letters well, what about other alphabetical letters, such as Russian, Arabic, Urdu, etc.?

---

### Post by Vaphell on 2013-04-16
doing homework for people is not allowed by the forum rules, we can only give hints

should work if you simply remove that *c in a_z* condition, because this is what filters out everything else.
Same approach can be used with bash or any other language supporting key->value relation

---

### Post by Lars Noodén on 2013-04-16
Here is one way to do it using [sed](http://manpages.ubuntu.com/manpages/quantal/en/man1/sed.1posix.html), sort and uniq which seems to be UTF-8 aware:

```

sed 's/\(.\)/\1\n/g' *filename* | tr '[:upper:]' '[:lower:]' | sort | uniq -c

```

---

### Post by GnuKian on 2013-05-23
I found a software specified for analysing text characters, here: [https://launchpad.net/kla/+download](https://launchpad.net/kla/+download)
Installing the "kla" in archlinux: "yaourt kla"

---

