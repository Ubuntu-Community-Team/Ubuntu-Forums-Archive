---
title: "[SOLVED] find matches in two files"
date: 2007-06-23
forum: General Help
---

### Post by borobudur on 2007-06-23
Hi there, 
it's quite difficult to find a name for our coming baby with my wife. 

There for I thought we could each one write the names in a file an find with one of the nice little unix programs the matches. But which one is it?

I'm sure there is a existing unix program to find matches in two files.

Can anyone help with this important family matter?
Thanks!

---

### Post by Cappy on 2007-06-23
how about
```
diff
```

```
NAME
       diff - compare files line by line

SYNOPSIS
       diff [OPTION]... FILES

DESCRIPTION
       Compare files line by line.

```

Congratulations on the baby too!

Edit: Actually this won't work ... =-/

Edit again:
Idea:
Merge the two files together like:
```
cat babynames1 >> babynames
cat babynames2 >> babynames

```
and then use uniq to find duplicate names and ignore case
```

sort babynames | uniq -di matchingbabynames
```
and it will output to a file called "matchingbabynames"

---

### Post by pickarooney on 2007-06-23
That's got to be the first time someone's used bash to name a baby :D

---

### Post by borobudur on 2007-06-23
I was also thinking about diff but didn't succeed.

Works perfect your suggestion Cappy! I let you know the results...

---

### Post by borobudur on 2007-06-26
Women! She wanted to see my list... :-(

---

