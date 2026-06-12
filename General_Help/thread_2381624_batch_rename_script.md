---
title: "batch rename script"
date: 2018-01-03
forum: General Help
---

### Post by mattdawolf on 2018-01-03
I am a newb with programming. Is there an easy way to trim the last five characters of a filename before the extension for an entire directory of files? Can't seem to bend krename to my will...

---

### Post by Holger_Gehrke on 2018-01-03
I don't know about krename, but rename in the shell will do what you want:
```
rename -n 's/.{5}\.([^.]*)$/.$1/' *
```
The option '-n' makes rename just show what it would do, to actually do the renaming leave that option out.

Holger

---

### Post by HermanAB on 2018-01-03
The Thunar file manager includes a graphical Bulk Rename utility that works.

---

### Post by mattdawolf on 2018-01-03
Awesome. Thanks!

---

### Post by vasa1 on 2018-01-03
> **mattdawolf said:**
> Awesome. Thanks!
What is awesome? Who is being thanked? In other words, what worked for you? The rename code provided by Holger_Gehrke works for me.

---

### Post by uRock on 2018-01-03
I use pyRenamer for bulk renaming.

---

