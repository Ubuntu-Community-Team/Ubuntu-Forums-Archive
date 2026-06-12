---
title: "mouse buttons / xbindkeys help"
date: 2007-05-17
forum: General Help
---

### Post by Subban on 2007-05-17
I've a Logitech MX1000 set up, but I'm not sure how relevant that will be to the actual problem here. Sometimes when I have rebooted the forward/back mouse buttons don't work, untill I change .xbindkeysrc mapping for them to buttons 6 and 7 then killall xbindkeys and restart it.

But then when I restart later, I have to change the buttons back to buttons 8 and 9. 

Any ideas why the buttons are changing, and how to fix it. Its not at every reboot but sporadically. 

Here is my current .xbindkeysrc

```
"/usr/bin/xvkbd -xsendevent -text "\[Alt_L]\[Left]""
  b:6
"/usr/bin/xvkbd -xsendevent -text "\[Alt_L]\[Right]""
  b:7
"echo ButtonPress 4 ButtonRelease 4 | xmacroplay -d 0 :0.0"
  b:11
"echo ButtonPress 5 ButtonRelease 5 | xmacroplay -d 0 :0.0"
  b:12
"echo ButtonPress 6 ButtonRelease 6 | xmacroplay -d 0 :0.0"
  b:13
"echo ButtonPress 7 ButtonRelease 7 | xmacroplay -d 0 :0.0"
  b:14
```

---

