---
title: "Volume and power buttons don't work"
date: 2018-04-04
forum: General Help
---

### Post by lukisforgets on 2018-04-04
Hi, please excuse me if this is in the wrong place, I'm very new to the forums and didn't know where to ask for support

I'm having the strangest of issues, I'm able to type fine, and mouse input works well, but all of the media controls on my keyboard don't work, neither do key commands like Ctrl+Alt+T (But Ctrl+C/V does), and the power button on my case doesn't work. They were all working fine before hand,  I rebooted and that fixed the problem one time, then after that it didn't work.

There doesn't seem to be any apparent cause, this was well over a month after my update to Ubuntu 17.10, I haven't changed hardware, the only thing that seems to coincide with it is my new controller (Third Party X-Bone Controller). But as we all know, correlation doesn't equal causation. I do have a script that runs at startup, but I made it a long time ago and it's never caused this, but it's listed below in case anyone was wondering. So I'm just really confused, any help would be appreciated, thank you.

Running: Ubuntu 17.10, almost exclusively on Unity Desktop

Script mentioned above: (tablet is not always plugged in when it tries to run)
```

[*]xinput set-prop "Wacom Bamboo 16FG 4x5 Finger touch" "152" 0

```

---

### Post by QIII on 2018-04-04
Moved to General Help.  You will likely attract more fish here.  :)

---

### Post by cruzer001 on 2018-04-04
Are you running xorg?

[https://itsfoss.com/switch-xorg-wayland/](https://itsfoss.com/switch-xorg-wayland/)

---

