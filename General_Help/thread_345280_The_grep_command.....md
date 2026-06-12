---
title: "The grep command...."
date: 2007-01-24
forum: General Help
---

### Post by Chillster on 2007-01-24
Need some commandline help pls...

I want to grep text from a file but i want to grep all the text between two values.
With grep -A 5 i get 5 lines following my value but i want to type two values and get the text in between like this:

1
2
3
this is the text
i want
5
6

Want to grep all text between 3 and 5, anyone have any idea how to do this?

---

### Post by Jussi Kukkonen on 2007-01-24
grep works on single lines, so you've got the wrong tool, I believe. You'll probably have to use  a real programming language -- awk might work, but so will any language that's any good with strings.

---

### Post by Chillster on 2007-01-24
Thanks for the reply! I read up on the awk command and that did the trick.

This is how for anyone who has the same problem:
 cat /etc/services | awk '/21/,/512/'  this will print everything from the line with 21 to the one 512 from /etc/services file.

---

