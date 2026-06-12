---
title: "Could not execute pmount error"
date: 2006-09-01
forum: General Help
---

### Post by Grog140 on 2006-09-01
When I try and mount my usb drive it instead gives me an error of not being ableto execute pmount.

Is it my system or is it my jump drive?

---

### Post by safeness on 2006-09-01
Ditto here. The error is happening on a relatively fresh install of the newest ubuntu (6.06 IIRC). The thumbdrive I am trying to mount is a Lexar Jumpdrive Secure, so there is a chance that could be the issue. Any help is greatly appreciated!

---

### Post by ifokkema on 2006-09-02
Did you guys try to execute the mount command from the console, or did you get this message after plugging in the drive?

---

### Post by Grog140 on 2006-09-02
When I plug in the device it doesn't automount like it used to so I have to click the icon (which I have on a panel) for it to mount, and then get the error. It used to work flawlessly when I plugged it in.

I can access the files but I need to look at my disks and set the usb drives access path as /tmp/whatever open nautilus as root, and then go to the drive location which is the /tmp/whatever I had to set beforehand.

Pretty annoying, lol.

---

### Post by ifokkema on 2006-09-02
Hm.... add yourself to the plugdev group:
```
sudo adduser <your_username> plugdev
```
log out, log in, and try again.

---

### Post by Grog140 on 2006-09-02
Thanks, it worked like a charm. Everything is back to normal.

---

