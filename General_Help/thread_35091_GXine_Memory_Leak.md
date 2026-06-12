---
title: "GXine Memory Leak?"
date: 2005-05-17
forum: General Help
---

### Post by Leav on 2005-05-17
Is this normal?

(this is after it played a loop of two mp3's for about two hours)

also, bear with me, because i'm not even sure what a memory leak is, i just heard it somewhere and assumed it meant that a program has some sort of bug that makes it eat up more memory and not freeing up unused memory (the kind of thing I do to amuse myself at comp-sci lessons)

(Edit: look at the first line the one with GXine)  :) 

Thanks!
-Leav

---

### Post by Sam on 2005-05-17
[QUOTE=Leav]Is this normal?

(this is after it played a loop of two mp3's for about two hours)

also, bear with me, because i'm not even sure what a memory leak is, i just heard it somewhere and assumed it meant that a program has some sort of bug that makes it eat up more memory and not freeing up unused memory (the kind of thing I do to amuse myself at comp-sci lessons)

(Edit: look at the first line the one with GXine)  :) 

Thanks!
-Leav[/QUOTE]
Yes, you are looking at the VM size, which is the size of every lib loaded by the application.
Go to Edit / Preferences and check the "Resident Memory" column. This is the real amount you are looking for.

BTW welcome here !

---

