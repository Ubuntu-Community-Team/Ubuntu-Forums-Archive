---
title: "cp, ls, rm command applied to filename &quot;-aba&quot;"
date: 2008-04-21
forum: General Help
---

### Post by hproc on 2008-04-21
Due to an error I created a file hwose name os "-aba" (a perfect legal unix name accodrding to the specifications), I tried to remove it 
but the command complains because it interprets the "-" in the name as an option !!! the same thing with ls , cp , mv. ¿Is it a bug or there is a way to deal with this? (I am using Ubuntu Gusty)

---

### Post by retrow on 2008-04-21
void.

---

### Post by Rocket2DMn on 2008-04-21
In terminal, navigate to the folder and run
```
rm ./-aba
```
to delete the file.

---

### Post by arguellodw on 2008-04-21
You can always use the drag & drop to trash can as well.  The rm ./-aba is a little more slick, though.

---

### Post by amingv on 2008-04-22
You can also put -- before it and it will not interpret it as a parameter.

```
rm -- -aba
```

Just to add to the answers.

---

### Post by Trail on 2008-04-22
Some interesting thing I just tested.

```

$ rm "-a"
rm: invalid option -- a
Try `rm ./-a' to remove the file `-a'.
Try `rm --help' for more information.

```

Heh, it's smart enough...

---

