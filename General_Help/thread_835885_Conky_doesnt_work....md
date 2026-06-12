---
title: "Conky doesnt work..."
date: 2008-06-20
forum: General Help
---

### Post by rossjman1 on 2008-06-20
I just installed Conky, and downloaded a simple .conkyrc file from one of the forums. Conky wont start for me. Nothing shows up at all.
```

jeff@jeff-laptop:~$ conky
Conky: use_spacer should have an argument of left, right, or none.  'yes' seems to be some form of 'true', so defaulting to right.
Conky: forked to background, pid is 10244
jeff@jeff-laptop:~$ 
Conky: desktop window (10000b5) is subwindow of root window (87)
Conky: window type - normal
Conky: drawing to created window (2600001)
Conky: drawing to double buffer

```
That's all that happens. Please help!

---

### Post by rossjman1 on 2008-06-20
Ok, Conky just randomly started working, but it doesn't start automatically with GNOME. I already have an entry in the Sessions window for conky. Am I missing something?

---

### Post by rossjman1 on 2008-06-22
Does anyone know how to get conky to automatically start with Gnome and Compiz?

---

### Post by hurricanejohn on 2008-06-26
you need a startup script for it that delays the start. i'll put it here so you can download it. i save it in my home directory and have it hidden but you should be able to run it anywhere

---

### Post by rossjman1 on 2008-06-26
Thanks! I was reading another thread which said you needed both, which is why it was screwing up.

---

