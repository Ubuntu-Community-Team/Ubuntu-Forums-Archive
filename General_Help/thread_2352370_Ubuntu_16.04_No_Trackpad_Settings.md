---
title: "Ubuntu 16.04 No Trackpad Settings"
date: 2017-02-11
forum: General Help
---

### Post by jonathan90 on 2017-02-11
I was using 14.04 and there was a glitch where using the trackpad would cause the whole screen to freeze at random times, so I followed the instructions on [this launchpad page]("https://bugs.launchpad.net/xorg-server/+bug/1220426/") to fix it. I ran this command.

[COLOR=#000000]echo "options psmouse proto=imps" | sudo tee /etc/modprobe.d/psmouse.conf >/dev/null
sudo modprobe -r psmouse && sudo modprobe psmouse

[/COLOR]After I ran it, it disabled any trackpad gestures and the mouse and trackpad shared the same move speed.

Now, I upgraded to 16.04 where the bug should be fixed, but the fix to the previous bug is still in effect and I can't adjust the trackpad or use it to scroll. Is there anyway I can reverse that command? Here is my settings menu. Notice that there's nothing on the trackpad. Thanks!

[http://i.imgur.com/7Zfil8a.png](http://i.imgur.com/7Zfil8a.png)

---

### Post by wildmanne39 on 2017-02-11
*Thread moved to **General Help**.*

---

### Post by jonathan90 on 2017-02-15
Bump. Still can't get it working.

---

