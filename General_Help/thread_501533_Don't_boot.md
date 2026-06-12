---
title: "Don't boot"
date: 2007-07-15
forum: General Help
---

### Post by Juan_CAT on 2007-07-15
Hello
Excuse my poor english
When botting, computer display a message, loading... or similar.
But if I wait two or three seconds, computer display this error: ata2.01: failed to set xfermode
and don't boot Kubuntu (Wubi)
Any solution for this problem?

---

### Post by ago on 2007-07-15
try to add `irqpoll` to c:\wubi\boot\grub\menu.lst in the line starting with "kernel"

see [http://fak3r.com/2007/06/22/failed-to-set-xfermode-solved/](http://fak3r.com/2007/06/22/failed-to-set-xfermode-solved/)

---

