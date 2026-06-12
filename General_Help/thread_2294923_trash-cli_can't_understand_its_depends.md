---
title: "trash-cli: can't understand its depends"
date: 2015-09-14
forum: General Help
---

### Post by vasa1 on 2015-09-14
*apt-cache show trash-cli* lists the "depends" of that package like this:```
Depends: python2.7, python (>= 2.7.1-0ubuntu2), python (<< 2.8), python-pkg-resources

```Why are there three versions of python? And what does "<<" mean? IIRC, "<<" normally means "much less than".

---

### Post by egeezer on 2015-09-14
It means you need python 2.7.*  in other words, anything in the 2.7 range, nothing earlier, nothing later.

---

### Post by Bashing-om on 2015-09-14
vasa1; Hello;

From my notes, and I failed to note the source:

The relations allowed are <<, <=, =, >= and >> for strictly earlier, earlier or equal, exactly equal, later or equal and strictly later, respectively. The deprecated forms < and > were used to mean earlier/later or equal, rather than strictly earlier/later, so they should not appear in new packages (though dpkg still supports them).

[INDENT][INDENT]hope this helps
[/INDENT][/INDENT]

---

### Post by vasa1 on 2015-09-14
> **Bashing-om said:**
> vasa1; Hello;

From my notes, and I failed to note the source:

The relations allowed are <<, <=, =, >= and >> for strictly earlier, earlier or equal, exactly equal, later or equal and strictly later, respectively. The deprecated forms < and > were used to mean earlier/later or equal, rather than strictly earlier/later, so they should not appear in new packages (though dpkg still supports them).

[INDENT][INDENT]hope this helps
[/INDENT][/INDENT]

That certainly does help. Thanks to both of you.

---

### Post by vasa1 on 2015-09-14
> **Bashing-om said:**
> ...
From my notes, and I failed to note the source:
...
Here you go: [https://www.debian.org/doc/debian-policy/ch-relationships.html](https://www.debian.org/doc/debian-policy/ch-relationships.html) (7.1 Syntax of relationship fields)

---

### Post by Bashing-om on 2015-09-14
vasa1; :)

> **vasa1 said:**
> Here you go: [https://www.debian.org/doc/debian-policy/ch-relationships.html](https://www.debian.org/doc/debian-policy/ch-relationships.html) (7.1 Syntax of relationship fields)

I should have remembered ! That link is 'bookmarked' - casual reading while awaiting.

[INDENT]documentation in linux is everywhere
[INDENT][INDENT]be careful what you read
[INDENT][INDENT][INDENT](does it apply)
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

