---
title: "Mysql formatting tables"
date: 2014-12-23
forum: General Help
---

### Post by johnnybgoode on 2014-12-23
I try to make a mini database in mysql. All data are input via ' Insert into books values ('title',' author','description');
So far so good, but the output isn't right. See example:
[ATTACH=CONFIG]258753[/ATTACH]

---

### Post by steeldriver on 2014-12-23
What output formatting are you expecting?

---

### Post by kpatz on 2014-12-23
The lines are wrapping since they're longer than the width of the terminal window.  Make the terminal window wider, or the font size smaller, and then it should fit without wrapping.

A graphical MySQL client would be better and easier.  Something like Workbench or phpMyAdmin.

---

### Post by beep3 on 2014-12-23
You could also try:

```
SELECT * FROM boeken \G
```

That will output everything vertically.

---

### Post by johnnybgoode on 2014-12-24
Indeed, making the terminal wider solved the problem.
Thanks

John

---

### Post by johnnybgoode on 2014-12-31
SOLVEDThank you.

[h=2]SOLVED     Thank yoy very much[/h]

SOLVED     Making the wide of the table larger did it. Again thank you.

---

