---
title: "&quot;grep -f&quot; usage"
date: 2013-10-03
forum: General Help
---

### Post by terminator14 on 2013-10-03
If I want to use "grep -f PATTERNS" to load patterns from a file, how do I tell it to ignore comments (lines that start with #) and blank lines from the PATTERNS file? 

Ex:

Command:
```
$ grep -f PATTERNS /etc/passwd
```


PATTERNS file:

```
sshd
www-data
list
#The following is a blank line

irc
nobody
#hplip

```

While the 2 comments are technically not ignored, they do not match anything because the pattern "#hplip" and "#The following is a blank line" do not appear in /etc/passwd, making it not as big a problem (though explicitly ignoring commented out lines would be better).
The blank line on the other hand matches everything. Without the blank line in the PATTERNS file, only 5 lines from /etc/passwd are returned. With the blank line, all the lines of /etc/passwd are returned! Is there any way to tell grep to ignore the blank lines in the PATTERNS file?

---

### Post by Vaphell on 2013-10-04
```
grep -f <( sed -r '/^#|^\s*$/d' patterns.txt ) /etc/passwd
```

---

### Post by terminator14 on 2013-10-04
> **Vaphell said:**
> ```
grep -f <( sed -r '/^#|^\s*$/d' patterns.txt ) /etc/passwd
```

Exactly what I was looking for - works awesome! Thanks!

---

