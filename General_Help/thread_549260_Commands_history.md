---
title: "Commands history"
date: 2007-09-12
forum: General Help
---

### Post by aitorcalero on 2007-09-12
Hello all,
I would like to know if it is possible to store terminal commands history between terminal session. I mean, I know that history commando can be used and also CTRL+r, but when you close your terminal, your commands list gets lost. :(

---

### Post by swisscow on 2007-09-12
Mine doesn't - I just press the arrow up key.

---

### Post by stchman on 2007-09-12
> **aitorcalero said:**
> Hello all,
I would like to know if it is possible to store terminal commands history between terminal session. I mean, I know that history commando can be used and also CTRL+r, but when you close your terminal, your commands list gets lost. :(

There is a file in your home folder I believed it is called .bash-history.  Use Nautilus View hidden files and you will see it.

---

### Post by jrmontg on 2007-09-12
vi /home/*yourusername*/.bash_history

---

### Post by stchman on 2007-09-12
> **jrmontg said:**
> vi /home/*yourusername*/.bash_history

Ok, it is an "_" instead of a "-".  I would also recommend the following command:

```
gedit ~/.bash_history
```

As vi is a very confusing editor at best.

---

