---
title: "Sort lines of text files"
date: 2006-08-15
forum: General Help
---

### Post by albox on 2006-08-15
Hi,
I'd like to sort lines of text files. Each line is composed of 2 columns seperated by a space. What I want to do is to sort lines using the second column which is a numeric value.
I know there is a command sort but it doesn't seem I can use it to do that. Do you have any idea to help me ?

Thank you ;)

---

### Post by Jussi Kukkonen on 2006-08-16
*man sort* helps.

If the data is as you say (so the column separators are the only whitespace)
*sort -n -k 2* should work.

---

