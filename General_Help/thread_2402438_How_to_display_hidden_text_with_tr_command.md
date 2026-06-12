---
title: "How to display hidden text with tr command ?"
date: 2018-09-29
forum: General Help
---

### Post by hanenb on 2018-09-29
Hi, it would be great if you can help me. I have a file, when I use the cat command, in the terminal I see that it's not empty as a file, it shows many spaces. I tried with the tr command by adding a backslash at the top of the text in order to delete special characters. But it's not  working.

---

### Post by again? on 2018-09-29
Does this work...
```
tr -d "[:space:]"
```

See 
```
man tr
```

---

### Post by HermanAB on 2018-09-30
I would use hexedit.

---

