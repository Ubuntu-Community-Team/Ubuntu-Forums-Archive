---
title: "Computer Name"
date: 2008-01-06
forum: General Help
---

### Post by AnthonyR on 2008-01-06
I recently installed 7.10 and neglected to give my computer a name. How do I give the computer a name now?
AnthonyR.

---

### Post by p_quarles on 2008-01-06
```
gksudo gedit /etc/hostname
```
The one word in this file will be the computer's name.

---

### Post by ryanVickers on 2008-01-06
wow haha try that in windows! ;)

Thats actually really useful if you need to change it to match a naming scheme on a lan or something...

---

### Post by Bllasae on 2008-01-06
> **ryanVickers said:**
> wow haha try that in windows! ;)
Actually, Windows is a LOT easier lol. Just right click My Computer, Properties, and then select the "Computer Name" tab and type in a new name.

---

### Post by jfinkels on 2008-01-06
> **Bllasae said:**
> Actually, Windows is a LOT easier lol. Just right click My Computer, Properties, and then select the "Computer Name" tab and type in a new name.

Easier than this?```
echo computername > /etc/hostname
```

---

### Post by ryanVickers on 2008-01-06
oh yeah lol I remember that... I just didn't think of it because I thought that that was only for changing workgroup and the computer "comment", ... ;)

---

### Post by Bllasae on 2008-01-06
> **jfinkels said:**
> Easier than this?
Yeah. A lot easier, actually :).

---

### Post by ryanVickers on 2008-01-06
> **jfinkels said:**
> Easier than this?```
echo computername > /etc/hostname
```

yeah exactly.... lol they have a thing for hiding features.. like the system restore is the worst - best feature , and probably most powerful in the OS and they hide it in accessories... so many things are there actually... system tools are not accessories!!! :mad:

;)

---

### Post by ryanVickers on 2008-01-06
> **Bllasae said:**
> Yeah. A lot easier, actually :).

not really :lolflag:

---

### Post by jfinkels on 2008-01-06
> **Bllasae said:**
> Yeah. A lot easier, actually :).

Different strokes for different folks.

---

### Post by Bllasae on 2008-01-06
> **ryanVickers said:**
> not really :lolflag:
Meh, if you're good at clicking a mouse.:lolflag:

---

### Post by ryanVickers on 2008-01-06
I am, but I'm the kind of guy who will shutdown from the terminal instead of the graphic, and type "sudo shutdown -h now" instead of just "sudo halt" :D

---

