---
title: "Installed a programme but can't find it."
date: 2008-03-21
forum: General Help
---

### Post by NovaAesa on 2008-03-21
I just installed an app package called 'python-gnuplot'.
All the dependancies installed as well, but now I can't find where to start the programme. I am using Linux Mint btw (I figure it should be the same for Ubuntu). If anyone could help me, this would be great.

---

### Post by kaboodle_fish on 2008-03-21
Does Alt + f2 then typing python-gnuplo in the search box not work?

---

### Post by NovaAesa on 2008-03-21
Nope, it says
> Could not open location 'file:///python-gnuplot'
The location or file could not be found.


---

### Post by StOoZ on 2008-03-21
have you tried:
> sudo find / -name python-gnuplot

maybe it can come up with something.

---

### Post by djgrandmarquis on 2008-03-21
You might also want to try:

```
whereis python-gnuplot
```

---

