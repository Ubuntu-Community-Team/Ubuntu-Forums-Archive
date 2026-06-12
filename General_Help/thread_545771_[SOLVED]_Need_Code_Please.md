---
title: "[SOLVED] Need Code Please"
date: 2007-09-08
forum: General Help
---

### Post by DougieFresh4U on 2007-09-08
I need to reconfigure X from recovery mode. Can some one please give me the exact code. It's been a while since I've done this, but I believe I boot into grub then go to recovery mode, type in code at prompt, then pretty much stay with defaults all through the X recovery. Is that correct? 
Thanks

---

### Post by user1397 on 2007-09-08
> **DougieFresh4U said:**
> I need to reconfigure X from recovery mode. Can some one please give me the exact code. It's been a while since I've done this, but I believe I boot into grub then go to recovery mode, type in code at prompt, then pretty much stay with defaults all through the X recovery. Is that correct? 
Thanksyes, go to recovery mode in grub; the command you're looking for is: ```
sudo dpkg-reconfigure xserver-xorg
```if that doesn't work, try it without sudo

---

### Post by merlinus on 2007-09-08
sudo dpkg-reconfigure xserver-xorg

-merlin

---

### Post by DougieFresh4U on 2007-09-08
Thanks very much.
Reconfiguring didn't solve my problem though. 
The problem is posted in my other thread on this page. Looking for suggestions

---

### Post by banewman on 2007-09-08
In the video card section of xserver-xorg try selecting vesa - it is a fail safe. :)

---

### Post by DougieFresh4U on 2007-09-08
> **banewman said:**
> In the video card section of xserver-xorg try selecting vesa - it is a fail safe. :)

Thanks, but that was the default one during reconfigure.
I really want to save my system, help please

---

### Post by banewman on 2007-09-08
Gotta start at the beggining then - what's the card? Can't see it from here. :)

---

### Post by DougieFresh4U on 2007-09-08
Please help!! See thread titled;
**"Power Outage"**

---

### Post by bodhi.zazen on 2007-09-08
Thread closed at OP request.

---

