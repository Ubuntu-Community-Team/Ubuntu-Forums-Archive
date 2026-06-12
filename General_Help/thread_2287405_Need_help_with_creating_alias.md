---
title: "Need help with creating alias"
date: 2015-07-19
forum: General Help
---

### Post by peter1897 on 2015-07-19
I am trying to create alias that when i change directory it will automatically list the content of the directory. I created this alias:

```
alias cs='cd;ls -l'
```

but if i run, for example: **cs /etc**, it lists the content of etc directory but doesn't switch to it.

How to make the alias to change the directory?

---

### Post by Habitual on 2015-07-19
```
alias cs='cd ; ls -l $_'
``` works here. [COLOR=#ff0000]Scratch that. It has "issues"[/COLOR]. Sorry.

---

### Post by peter1897 on 2015-07-19
Is it possible this to be done with function if it is not possible with alias?

---

### Post by Lars Noodén on 2015-07-19
A function would be easy.

```

cs() { cd $@; ls -l; }

```

---

### Post by peter1897 on 2015-07-19
Thanks, it's working.

---

