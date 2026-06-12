---
title: "Script Help (Probably Easy Question)"
date: 2008-06-29
forum: General Help
---

### Post by RATM_Owns on 2008-06-29
I'm making a script and one thing it is supposed to do is open a file (with sudo privileges) and replace all appearances of it with another word.
Is this possible?

(If not, I'll just put in instructions and open a sudo gedit)

---

### Post by mempman on 2008-06-29
Its possible with using sed.

Here is an example:
```

nano@nano-laptop:~$ echo "hello" | sed  s/he/yahoo/
yahoollo

```

---

