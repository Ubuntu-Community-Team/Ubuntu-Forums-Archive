---
title: "Makefile problem"
date: 2008-06-10
forum: General Help
---

### Post by Black Mage on 2008-06-10
I am having this make file error that says: 

Makefile:37: *** missing separator.  Stop.

and line 37 looks like this:

```

# Only set debug if DEBUG is set

.IF $(DEBUG) == 1

CFLAGS =-g -W"c,debug,LANGLVL(EXTENDED)"

.ELSE #<-Line 37

CFLAGS =-W"c,LANGLVL(EXTENDED)"

.END

```

So could anyone please give me some guidance on what is wrong here?

Thanks

---

### Post by Dr Small on 2008-06-10
I don't know anything about this, but if .ELSE is causing the problem, analyse the line above it.

---

### Post by Black Mage on 2008-06-10
> **Dr Small said:**
> I don't know anything about this, but if .ELSE is causing the problem, analyse the line above it.

When I comment that line out, it still throws the problem. But if I comment the .ELSE out, the problem is gone.

---

