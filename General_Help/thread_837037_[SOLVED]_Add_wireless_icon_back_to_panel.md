---
title: "[SOLVED] Add wireless icon back to panel"
date: 2008-06-22
forum: General Help
---

### Post by brett123 on 2008-06-22
I deleted my wireless network icon from the top panel. How can I add it back? (Not sure what the application is called).

Thanks.

---

### Post by angry_johnnie on 2008-06-22
The wireless icon itself would be:


```
nm-applet --sm-disable
```


But then, that's not really something you add to the panel...

What you're missing is probably the notification area.

Right-click on the panel, and choose **add to panel**, then look for **notification area**, and click on the add button.  Then you can launch nm-applet.

---

### Post by wormser on 2008-06-22
Right click on the panel> Add to Panel> Notification Area.

---

### Post by brett123 on 2008-06-22
Thanks guys, that did it.

I was looking for "wireless" or "network" etc, didn't even think to try "notification area".

---

