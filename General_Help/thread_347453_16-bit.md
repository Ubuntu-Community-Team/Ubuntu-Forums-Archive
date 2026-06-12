---
title: "16-bit"
date: 2007-01-27
forum: General Help
---

### Post by DougieFresh4U on 2007-01-27
\\:D/ \\:D/ Some games require 16-bit. Where and how do I change that and will that allow me Direct Rendering?

---

### Post by taurus on 2007-01-27
You change it in /etc/X11/xorg.conf.  I believe the default is 24 so just change that to 16, perhaps.

---

### Post by DougieFresh4U on 2007-01-27
Thank you. Will that cause me any drama when I shut down and restart? Also how do access etc/whatever to change?

---

### Post by taurus on 2007-01-27
```
sudo nano -w /etc/X11/xorg.conf
```
<Ctrl>x to exit and Y to save it.

---

### Post by DougieFresh4U on 2007-01-27
> **taurus said:**
> ```
sudo nano -w /etc/X11/xorg.conf
```
<Ctrl>x to exit and Y to save it.

Thanks, now will that help Direct Rendering as I read some where that Direct Rendering needed 16-bit to enable it?

---

### Post by taurus on 2007-01-27
Make the change, reboot, and see what happens.  If it doesn't work, change it back to 24.  That's the best way to test it out yourself.

---

### Post by DougieFresh4U on 2007-01-27
I have xorg conf up. is it in "screen" that I change. it says default depth 24. is that the one I change?

---

### Post by taurus on 2007-01-27
Yip.  Replace 24 with 16 and see what happens after reboot.  X should run fine but can you play whatever game you intended to play initially?

---

### Post by DougieFresh4U on 2007-01-27
Done deal, works great.**Thanks taurus!!** BTW:I have left sunny Florida to help my Mom's out Been a busy week.):P

---

### Post by taurus on 2007-01-27
I thought you said NY was just a little toooooooo cold for you!

---

