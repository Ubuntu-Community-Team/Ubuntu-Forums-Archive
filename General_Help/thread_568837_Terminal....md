---
title: "Terminal..."
date: 2007-10-06
forum: General Help
---

### Post by Snufkin UK on 2007-10-06
Finally got Ubuntu working. YES! And now having problems adding to sources.list in the terminal.

Every time I try to edit it, it just deletes lines already in there and wont let me type, why am I failing so bad?

Thanks in advance. :)

---

### Post by PmDematagoda on 2007-10-06
In order to edit system files you need to put sudo infront, for example to edit the sources file:-

```
sudo gedit /etc/apt/sources.list
```

---

### Post by Snufkin UK on 2007-10-06
Just tried that, it deletes lines already in there instead of letting me edit. :S

---

### Post by taurus on 2007-10-06
What do you mean it deletes lines already in there?  It will not delete anything unless you tell it to from a keyboard or a mouse.

```
gksudo gedit /etc/apt/sources.list
```

---

### Post by Snufkin UK on 2007-10-06
Well when I try to add something, it writes it over another line. :S Or appears to be.

---

### Post by taurus on 2007-10-06
Can you post a screenshot of it?

---

