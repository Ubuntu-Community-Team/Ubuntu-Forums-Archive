---
title: "How to open Rhythmox"
date: 2014-07-24
forum: General Help
---

### Post by pinklemon on 2014-07-24
Hello!
I downloaded some youtube songs form youtube to mp3 and avi, but I cant hear ahything.

Pleas, what is the problem?
Many thanks!!!

---

### Post by sotiris2 on 2014-07-24
Does rhythmbox open but can't play the files? Does it not?  Do you have any other mp3 from another source and if so can rhythmbox play them?

With what program are you trying to play the avi files?

---

### Post by Rob Sayer on 2014-07-25
Did you install the restricted codecs?  If not copy and paste into terminal:

```
sudo apt-get update
```

enter password and then

```
sudo apt-get install ubuntu-restricted-extras
```

That's one of the first things I always do in a ubuntu install.

---

