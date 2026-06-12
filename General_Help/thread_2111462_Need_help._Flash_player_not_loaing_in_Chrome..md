---
title: "Need help. Flash player not loaing in Chrome."
date: 2013-02-02
forum: General Help
---

### Post by garnedi on 2013-02-02
Some body please help me. I'm using Ubuntu 10.04. Flash player worked well till last night. This morning when I turned on youtube it's showing "couldn't load plug-in" message. I'm attaching Screen shot of the message.

I tried re installing both chrome and adobe flash player but it didn't work.

---

### Post by varunendra on 2013-02-02
It seems you have got your problem solved as per this post :
> **garnedi said:**
> ***SOLVED***

goto chrome://plugins/
click on details (top right)
disable adobe flash player

Name:	Shockwave Flash
Version:	11.5.31.138

then restart the browser.

hope this'll work.


If so, please mark this one as [Solved] using "Thread Tools" link above.

Thank You.

---

### Post by Horbo on 2013-02-02
Just delete (or rename if you're paranoid/cautious) ~/.config/google-grome/PepperFlash/

Restart chrome.

Problem fixed.

---

