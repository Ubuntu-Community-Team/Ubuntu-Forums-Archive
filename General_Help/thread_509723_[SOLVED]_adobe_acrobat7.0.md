---
title: "[SOLVED] adobe acrobat7.0"
date: 2007-07-25
forum: General Help
---

### Post by rbprogrammer on 2007-07-25
i installed [adobe acrobat7.0]("http://www.adobe.com/products/acrobat/readstep2.html") from the [FONT="Courier New"].tar.gz[/FONT], but when i go to run the adobe program i get:
```

expr: syntax error
expr: syntax error
expr: syntax error
expr: syntax error
expr: syntax error
expr: syntax error
...
and it goes on forever
...
expr: syntax error
expr: syntax error

```
did anyone get adobe acrobat7.0 to work correctly??

---

### Post by confused57 on 2007-07-25
You might want to add the Medibuntu repositories and install acroread:
[http://www.medibuntu.org/repository.php](http://www.medibuntu.org/repository.php)

---

### Post by mannheim on 2007-07-25
There's a fix for this. You need to open up the script /usr/local/Adobe/Acrobat7.0/bin/acroread in a text editor, using sudo, and make the change described [[COLOR="Blue"]here[/COLOR].]("http://javier.rodriguez.org.mx/index.php/2007/06/01/fix-adobe-acrobat-readers-expr-syntax-error-message/")

---

