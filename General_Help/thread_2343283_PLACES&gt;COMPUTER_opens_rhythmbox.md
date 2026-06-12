---
title: "PLACES&gt;COMPUTER opens rhythmbox"
date: 2016-11-14
forum: General Help
---

### Post by Dave.B on 2016-11-14
when i go to places>computer i get rhythmbox  
how can i fix this?

---

### Post by QIII on 2016-11-15
Hello!

You might make it easier for others to help if you would let everyone know which release you are using.

---

### Post by Dennis N on 2016-11-15
That used to be a problem with some past releases of Ubuntu MATE (I experienced it myself). It can be easily fixed in that system. What are you using?

---

### Post by Dave.B on 2016-11-21
i am using mate 1.12.1 nor sure the ubuntu version

---

### Post by howefield on 2016-11-21
> **Dave.B said:**
> i am using mate 1.12.1 nor sure the ubuntu version

Posting the output of 

```
cat /etc/*-release
```

will tell us.

---

### Post by Dennis N on 2016-11-21
_Problem to be fixed:_

**MATE menu > Places > Home (or any other folder)** opens the folder in an application (in my case, Audacious, but I have seen reports of other things opening).

_Solved by:_

Open file manager, then using any folder: right click > Open With > Other Application > Caja (there were two Cajas to choose from: one with a folder symbol, the other with the file cabinet symbol. I selected the latter). 

This fixed the problem. My log entry refers to this being done in Ubuntu MATE 14.10, but try it with your version. Can't hurt.

---

