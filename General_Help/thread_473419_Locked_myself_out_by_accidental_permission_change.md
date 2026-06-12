---
title: "Locked myself out by accidental permission change"
date: 2007-06-14
forum: General Help
---

### Post by Ariox on 2007-06-14
Title says it all... I did a groggy "sudo chmod 770 -R /". I don't know what I was thinking. I can't boot into a gui. I can get into recovery mode, but when I set the permissions there it doesn't seem to last after reboot. (?)

:edit: Permissions Do stay the same, but my system hangs when trying to start the gui. I get a black screen and round loading icon indefinitely. :(

Using FF 7.04

--Ariox

---

### Post by revertex on 2007-06-14
fix /tmp ~/home permissions, at least **chmod**  -Rf 1777 /**tmp**

---

### Post by Ariox on 2007-06-14
I ran <chmod 177 -Rf /tmp /home>. No change in symptoms.

---

### Post by revertex on 2007-06-14
i mean

```
chmod  -Rf **1777** /tmp
```

not 

```
chmod  -Rf **177** /tmp
```

---

