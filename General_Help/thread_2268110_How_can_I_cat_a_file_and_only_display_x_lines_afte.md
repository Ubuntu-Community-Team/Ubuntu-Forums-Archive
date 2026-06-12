---
title: "How can I cat a file and only display x lines after a pattern is found"
date: 2015-03-06
forum: General Help
---

### Post by matt174 on 2015-03-06
Once cat reaches a heading, like "Class A", I would want to print the next 10 lines - nothing before the heading, and nothing after the 10 lines that proceed the heading.

Thanks!

---

### Post by Lars Noodén on 2015-03-06
You could use [grep](http://manpages.ubuntu.com/manpages/trusty/en/man1/grep.1.html) with the -A option.

```

grep -A 10 foo /path/to/somewhere/somefile.txt

```

---

### Post by nerdtron on 2015-03-06
```
cat filename.txt | grep -A 10 "Class A"
```
-A to display 10 lines after the pattern is found
-C to display 10 lines before and after, the pattern is on the center
-B to display 10 lines before the pattern is found

---

### Post by matt174 on 2015-03-06
Thanks a lot!

---

### Post by matt174 on 2015-03-06
Thanks for the very thorough reply!

---

