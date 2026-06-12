---
title: "Quick QUESTION"
date: 2007-09-06
forum: General Help
---

### Post by The Wisedude on 2007-09-06
In a script how what is the command to make it press the "return" key.

This key:

[IMG]http://i1.tinypic.com/4zbz3uf.png[/IMG]

---

### Post by The Wisedude on 2007-09-06
Bump I need to know this please, someone?

---

### Post by Lord Illidan on 2007-09-06
I didn't quite catch your meaning. You want the script to press the ENTER key or you want the script to prompt the user to press the ENTER key?

---

### Post by The Wisedude on 2007-09-06
I want the key to PRESS enter key :) Help please.

---

### Post by The Wisedude on 2007-09-07
Bump

---

### Post by ghantoos on 2007-09-07
what kind of script are you talking about?

shell? python? perl? etc..

the ENTER is usually replaced by \n

dunno if this helps,

cheers,

ghantoos

---

### Post by praet on 2007-09-14
see: 
[http://ubuntuforums.org/showthread.php?t=527974](http://ubuntuforums.org/showthread.php?t=527974)

So to send the enter key you could use xvkbd and this string "\r" :
```
xvkbd -text "\r"
```

---

