---
title: "Searching multiple string using grep"
date: 2008-05-05
forum: General Help
---

### Post by retrow on 2008-05-05
I'm running a program which outputs results to a log file. I wasn't keeping track of some of changes which I should have. Now I want to search through a list of parameters through a list of log files.

The question is how can I use multiple patterns in a single grep command. One option is running them one after the other, but I was wondering whether we can have multiple patterns within a single grep command.

Thanks.

---

### Post by brownicb on 2008-05-05
cat /etc/passwd | grep "user1\|user2"

---

### Post by bwhaley on 2008-05-05
Can you use a the | regular expression syntax. For example, you could do something like:

grep "[a|b|c]" <files>

This will return any lines that have the characters a, b or c.

---

### Post by retrow on 2008-05-05
Thanks guys. That was just what I was looking for.

The missing part in my puzzle was the use of | between patterns.

---

