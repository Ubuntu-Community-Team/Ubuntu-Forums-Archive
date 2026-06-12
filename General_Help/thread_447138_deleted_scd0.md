---
title: "deleted scd0"
date: 2007-05-17
forum: General Help
---

### Post by fAlCoNNiAn on 2007-05-17
hey guys,

i accidentaly deleted my scd0 folder in the /dev/ section. i tried to recreate it, but not sure what chmod to use and what not. im now unable to mount any optical media thats inserted into my drive.:(

can someone guide me on making it work again? thanks in advance.

---

### Post by rbmorse on 2007-05-17
remove all references to scd0 in /dev and reboot. It should get detected and the device node recreated automagically

---

