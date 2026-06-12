---
title: "2 network icons, Network vs nm-tray"
date: 2019-05-13
forum: General Help
---

### Post by ProDigit on 2019-05-13
After the upgrade from 18.04 to 18.10, I'm left with 2 network icons.
Network and nm-tray.

What's the best one, and can I remove one in LXQT session settings, without breaking it?

---

### Post by ProDigit on 2019-06-16
Bump?
And btw, I don't believe this post was made 4 weeks ago. More like 4 months ago.

---

### Post by ardouronerous on 2019-06-17
[IMG]https://i.imgur.com/GY2ezBR.png?1[/IMG]
Is your problem similar to this?

If so, I discovered a workaround through this: [https://ubuntuforums.org/showthread.php?t=2387434&p=13750208#post13750208](https://ubuntuforums.org/showthread.php?t=2387434&p=13750208#post13750208)

My solution is this:

```
[Desktop Entry]
Version=1.1
Type=Application
Name=pkill nm-applet && nm-applet &
Exec=sh -c "sleep 10 && pkill nm-applet && nm-applet &"
```

I created this launcher and placed it in [FONT=system]/.config/autostart/[/FONT]. Restart your PC. The two network icons should appear and vanish after 10 seconds, leaving only one network icon. I gave it a 10 second delay because when I tried it without the delay, it didn't work.

---

