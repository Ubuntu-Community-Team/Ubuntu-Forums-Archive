---
title: "[SOLVED] check system resources in terminal?"
date: 2008-03-30
forum: General Help
---

### Post by HappyFeet on 2008-03-30
i need to know how much ram/disk space im using. because im using openbox, i need to do it in the terminal. thanks.

---

### Post by scragar on 2008-03-30
run ```
free -m
```
to see how many meg's of ram are used where, same for swap.

---

### Post by HappyFeet on 2008-03-30
thanks, but what about disk space usage?

---

### Post by adult swim on 2008-03-30
from terminal run
```
top
```
to get out of that hit q

---

### Post by edolfo on 2008-03-30
I was looking for an answer for this myself, and out of curiosity, I went to System > Help and Support.  I wasn't really expecting much, but the last entry was exactly what I was looking for.

The command I think you are looking for is df.  Type man df for the manual page.

I needed to check the space on the drive Ubuntu calls "hdd1", so I used the following:

df -h /media/hdd1/

With the "h" flag there for human-readable output.

---

### Post by scragar on 2008-03-30
```
sudo du --apparent-size -h -s  /
```
will work out total hd usage. Takes a long time though.
ooh, looks like df works:
```
df -h /
```

---

### Post by HappyFeet on 2008-03-30
thanks for the help guys. you're the best.

---

