---
title: "Disable rcS scripts?"
date: 2007-07-10
forum: General Help
---

### Post by KyleBrandt on 2007-07-10
Does anyone know a good way to manage   /etc/rcS.d/     scripts.  I want to disable some of them from start up, but want to to be able to reactive them when it suits me.  I noticed that the BootUp-Manager will not allow this.

---

### Post by bodhi.zazen on 2007-07-10
Linux is case sensitive, so ....

Rename the script with a small s

then, to re-activate, you can rename back to a large S

---

### Post by KyleBrandt on 2007-07-10
```
/etc/rcS.d$ sudo rename S41tspc s41tspc
Bareword "S41tspc" not allowed while "strict subs" in use at (eval 1) line 1.
```

I tried:  ```
]sudo ./S41tspc stop
``` but still got the error...

---

### Post by bodhi.zazen on 2007-07-10
:lolflag:

Sorry about that m8

```
sudo mv S41tspc s41tspc
```

---

### Post by KyleBrandt on 2007-07-11
Thanks, that did it!  Can you explain why move worked and rename didn't?

---

### Post by bodhi.zazen on 2007-07-11
[http://kangry.com/topics/viewcomment.php?index=538](http://kangry.com/topics/viewcomment.php?index=538)

So you could try ```
sudo remane S s *tscp
```

---

