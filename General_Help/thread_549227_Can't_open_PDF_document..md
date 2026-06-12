---
title: "Can't open PDF document."
date: 2007-09-12
forum: General Help
---

### Post by aaargh486 on 2007-09-12
If I try to open a certain (only happens with one) PDF document, it open a messagebox with "Couldn't open blablabla: Error 3".
The terminal gives this:

```
aaargh486@SPHERE:~/Downloads$ evince Mc\ graw\ Hill\ -\ Hacking\ Linux\ Exposed.pdf 
Error: Document has not the mandatory ending %EOF
Error: Document has not the mandatory ending %EOF
aaargh486@SPHERE:~/Downloads$ 

```

Why does this happen? I can open any other PDF document correctly, only this one complains.

---

### Post by eggdeng on 2007-09-12
Probably a bad file. If you are using evince, you might try downloading acrobat from [http://www.adobe.com/support/downloads/product.jsp?product=10&platform=unix]("http://www.adobe.com/support/downloads/product.jsp?product=10&platform=unix") It's a lot more feature-full.

---

