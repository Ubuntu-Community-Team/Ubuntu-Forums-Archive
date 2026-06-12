---
title: "How do I make notifications on Lubuntu 13.04?"
date: 2013-10-10
forum: General Help
---

### Post by vasa1 on 2013-10-10
I want to know how to make a notification on Lubuntu 13.04. I'm mentioning the distro flavor because I think Ubuntu handles notifications differently than Xubuntu and Lubuntu.

I can get this (from [https://wiki.archlinux.org/index.php/libnotify](https://wiki.archlinux.org/index.php/libnotify)) to work:```
#!/usr/bin/env python
from gi.repository import Notify
Notify.init ("Hello world")
Hello=Notify.Notification.new ("Hello world","This is an example notification.","dialog-information")
Hello.show ()
```but this doesn't:```
#!/usr/bin/env bash
notify-send 'Hello world!' 'This is an example notification.'
```I get```
/home/vasa1/bin/hw.sh: line 2: notify-send: command not found
```I've tried using **xfce4-notifyd** in place of **notify-send** and that fails as well with```
/home/vasa1/bin/xfcehw.sh: line 2: xfce4-notifyd: command not found
```

---

### Post by vasa1 on 2013-10-10
Installing **libnotify-bin** seems to get things going. Then notify-send worked, but xfce4-notifyd didn't and that doesn't matter now.

---

