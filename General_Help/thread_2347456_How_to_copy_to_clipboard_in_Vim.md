---
title: "How to copy to clipboard in Vim"
date: 2016-12-25
forum: General Help
---

### Post by flex567 on 2016-12-25
I tried this sequence of commands but I couldn't paste the text into Geany from Vim

```

:set nonumber
<Shift> v 
<Shift> g
"*y

```

After that I wasnt able to paste the text to Geany??

---

### Post by zacktu on 2016-12-25
If I want to copy something from vim I highlight the section to copy and type Ctrl-Shift-c.  If I want to paste into vim I go into insert/append mode at the appropriate insert point and type Ctrl-Shift-v.

---

### Post by flex567 on 2016-12-25
> Ctrl-Shift-c Doesnt work in Gvim

I found other way anyway, with "+y

---

