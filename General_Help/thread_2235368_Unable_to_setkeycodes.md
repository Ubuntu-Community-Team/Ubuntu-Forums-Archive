---
title: "Unable to setkeycodes?"
date: 2014-07-20
forum: General Help
---

### Post by ojdon on 2014-07-20
Hi there

I purchased a second hand dell duo off of eBay last week and hastily installed Ubuntu 14.04 + Gnome-shell over Windows 8. It is a great little netbook. One of the unique features about this netbook is that it has the screen on a hinge so it can be collapsed down into a "tablet mode". When the screen is flipped it can send two inputs to register the tablet mode "enabled" or "disabled". 

After following guides such as [this]("https://help.ubuntu.com/community/dell-duo/inspiron-1090") or [this]("http://jeffhoogland.blogspot.co.uk/2011/08/howto-linux-on-dell-inspiron-duo.html") they say to insert those two lines into rc.local and reboot. When I go and set the shortcut by flipping the screen around it doesn't seem to register the screen flipped or not. I have tried to manually enter (as root) the commands but still no luck. Has the way to setting keycodes changed since the guide was originally written?

Any help?

Thanks!

---

### Post by tgalati4 on 2014-07-21
The guide you referenced should map two keys to tablet mode on or off.  You have to go into keyboard shortcuts and assign actions (it doesn't say what scripts specifically) to the two keys:  XF86LAUNCH1 and XF86LAUNCH2

Open a terminal:

```
cat /etc/rc.local
```

Be sure the commands are put above the "exit 0" line otherwise they don't get seen.

---

### Post by ojdon on 2014-07-21
Here is my rc.local. Everything appears to be correct. I've rebooted and then assigned a new custom shortcut to launch onboard, but when I go assign a new accelerator it doesn't seem to detect the new keycodes. I have also ran "xev" but it doesn't detect the keycodes either. :/

---

### Post by tgalati4 on 2014-07-21
Try:

```
sudo showkey -s
```

Press a few keys, then try flipping and see what keycodes show up.

---

### Post by ojdon on 2014-07-22
It doesn't seem to detect the set keys either. :/

---

