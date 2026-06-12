---
title: "sort: union, intersection, and ???"
date: 2015-10-08
forum: General Help
---

### Post by vasa1 on 2015-10-08
I was reading [https://github.com/jlevy/the-art-of-command-line](https://github.com/jlevy/the-art-of-command-line) and I found this:```
      cat a b | sort | uniq > c   # c is a union b
      cat a b | sort | uniq -d > c   # c is a intersect b
      cat a b b | sort | uniq -u > c   # c is set difference a - b
```Could someone please explain the third line?

---

### Post by Lars Noodén on 2015-10-08
By itself, and assuming a sorted input, [uniq](http://manpages.ubuntu.com/manpages/trusty/en/man1/uniq.1.html) prints out each line once.  With the -u option, only those lines that are not repeated are printed.  It is the opposite of -d.  So *cat a b | sort | uniq -u > c* would eliminate the lines that are in both set a and b, in other words a XOR b.  By repeating b and using -u, it guarantees that anything in b is eliminated from the final list, whether or not it is also in a, in other words a - b.

---

### Post by vasa1 on 2015-10-08
> **Lars Noodén said:**
> By itself, and assuming a sorted input, [uniq](http://manpages.ubuntu.com/manpages/trusty/en/man1/uniq.1.html) prints out each line once.  With the -u option, only those lines that are not repeated are printed.  It is the opposite of -d.  So *cat a b | sort | uniq -u > c* would eliminate the lines that are in both set a and b, in other words a XOR b.  **By repeating b** and using -u, it guarantees that anything in b is eliminated from the final list, whether or not it is also in a, in other words a - b.
Thank you for explaining :)

---

### Post by Lars Noodén on 2015-10-08
No problem. 

By the way,  I notice that [cat](http://manpages.ubuntu.com/manpages/trusty/en/man1/cat.1.html) is unnecessary there.  The utility [sort](http://manpages.ubuntu.com/manpages/trusty/en/man1/sort.1.html) can read files directly:

```

sort a b | uniq > c
sort a b | uniq -d > c
sort a b b | uniq -u > c

```

---

### Post by vasa1 on 2015-10-08
> **Lars Noodén said:**
> No problem. 

By the way,  I notice that [cat](http://manpages.ubuntu.com/manpages/trusty/en/man1/cat.1.html) is unnecessary there. ...
Then it's another case of UUOC: [http://porkmail.org/era/unix/award.html](http://porkmail.org/era/unix/award.html) and [http://stackoverflow.com/questions/11710552/useless-use-of-cat](http://stackoverflow.com/questions/11710552/useless-use-of-cat)

---

