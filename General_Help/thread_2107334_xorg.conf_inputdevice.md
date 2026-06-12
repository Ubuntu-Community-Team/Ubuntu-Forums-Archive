---
title: "xorg.conf inputdevice"
date: 2013-01-21
forum: General Help
---

### Post by Zirts on 2013-01-21
Hi,

Can anyone confirm that it is possible to use this line in xorg.cong

```
Option "ButtonMapping" "1 2 3 6 7 8 9"
```

Will it then execute it every time X starts and apply it to my mouse?

And second question would be that my mouse has it so that its button mapping is by default ```
1 2 3 4 5 6 7 8 9 10 11 12 13 14 15
```
Now the 4 and 5 are scroll wheel up and down. But if I put 8 9 or 10 11 instead of 4 5 then I will have my 2 bonus buttons working but no mouse wheel. So If i have this line after the button mapping line:
```
Option	    "ZAxisMapping" "4 5"
``` will I now have both scroll working and the extra buttons working also.

---

