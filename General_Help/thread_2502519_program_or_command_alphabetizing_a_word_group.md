---
title: "program or command alphabetizing a word group?"
date: 2024-11-18
forum: General Help
---

### Post by ubto66 on 2024-11-18
This is a group of words:
fast fine deal up here
The words are placed one after another and with 1 space between them.
Is there a program or command that will sort such a string of words in alphabetical order and the
output format is one word after another and 1 space between each word.
I got aware of the sort command. But it outputs in columns and I do not know how to change
that. Thank you.

---

### Post by Holger_Gehrke on 2024-11-18
Use the 'tr' command to **tr**anslate the spaces into newlines, then 'sort' then the inverse translation.
```

echo 'car fine deal up here'|tr ' ' '\n'|sort|tr '\n' ' '

```
will show 'car deal fine here up'.

Holger

---

