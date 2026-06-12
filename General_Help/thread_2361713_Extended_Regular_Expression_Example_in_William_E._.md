---
title: "Extended Regular Expression Example in William E. Shotts' The Linux Command Line"
date: 2017-05-19
forum: General Help
---

### Post by John_Patrick_Mason on 2017-05-19
I don't understand what the second plus sign does in the following extended regular expression and why it's necessary:

```
echo "This that" | grep -E '^([[:alpha:]]+ ?)+$'
```

Could somebody help me? The regular expression is supposed to match groups of one or more alphabetic characters separated by single spaces. Why can't I just omit the second plus sign?

---

### Post by steeldriver on 2017-05-20
Did you try it? Without the second +, it will only match a *single *group of one or more alphabetic characters (optionally followed by a single space):

```

~$ echo "This" | grep -E '^([[:alpha:]]+ ?)$'
This
~$ echo "This or that" | grep -E '^([[:alpha:]]+ ?)$'
~$ echo "This or that" | grep -E '^([[:alpha:]]+ ?)**+**$'
This or that

```

---

