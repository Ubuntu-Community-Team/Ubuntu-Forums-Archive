---
title: "How to customize the AMOR creatures"
date: 2015-01-19
forum: General Help
---

### Post by nickrocks24 on 2015-01-19
I recently stumbled upon a program called AMOR on the software centre. I was wondering where the little animals were saved so my friend could edit them. Thanks in advance.

---

### Post by Holger_Gehrke on 2015-01-19
I can't tell you, but I can tell you how to find out yourself.
Open a terminal and at the prompt type
```

dpkg-query -L amor

```
you should get a list of all files installed by the package in the terminal. When you're done with the list type 'exit' to close the terminal.

---

