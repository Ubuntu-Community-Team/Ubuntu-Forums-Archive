---
title: "Left click works when it wants."
date: 2015-11-06
forum: General Help
---

### Post by sdamian9025 on 2015-11-06
I'm running Ubuntu 14.04.3 and using cinnamon desktop environment. Sometimes, the left click will stop working at random times, for seemingly no reason. The right click and touchpad aren't affected though. When it stops working, it's like it's still pressed down (drags things across the screen). Note: my usb mouse is affected as well. To fix this, I have to run:```

sudo -s
a=0
while [ $a == 0 ]; do
modprobe -r psmouse
modprobe psmouse
done

```
as soon as I log in. This disables drag-drop capabilities though. Any thoughts?

---

