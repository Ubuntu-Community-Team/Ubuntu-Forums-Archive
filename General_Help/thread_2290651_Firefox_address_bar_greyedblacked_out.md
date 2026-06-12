---
title: "Firefox address bar greyed/blacked out"
date: 2015-08-14
forum: General Help
---

### Post by rdh61 on 2015-08-14
After a Firefox package upgrade (to version 40.0) I cannot solve the problem of the address bar being greyed/blacked out. The previous fix (about:config -> gfx.xrender.enabled = false) which worked on the previous Firefox version, results in the whole window being blank as described [here]("http://ubuntuforums.org/showthread.php?t=2290528"). The other fix suggested [here]("http://ubuntuforums.org/showthread.php?t=2244521") (xorg.conf file) makes no difference. Please can somebody suggest something else? Thank you.

---

### Post by kerry_s on 2015-08-14
have you tried changing themes/appearance ?

---

### Post by Bucky Ball on 2015-08-14
You are using Lubuntu 14.04 and did you install Firefox 40.0 from the official Ubuntu repos?

* Update: Right, just checked. 40.0 seems to be the one in the repos. From the links you posted seems like this is an issue shared by others and may be a bug. Have you tried doing a full update/upgrade today?

```


sudo apt-get autoremove
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
```

---

### Post by Habitual on 2015-08-14
Maybe this [1]("http://bournetoraiseshell.com/article.php?story=20140609132431847") year old clue?
Open new tab...
```
type about:config[Enter] 
Promise to be careful 
In the Search Bar type gfx.xrender.enabled 
Right-click (F12) and Toggle to make it false
restart browser.
```

but [8/13/15 8:51 AM]("https://support.mozilla.org/en-US/questions/1077576#answer-766766") says he used "true"

---

### Post by rdh61 on 2015-08-14
Thanks for your replies. It seems the xorg.conf file has worked after all... after a reboot. (When WILL I EVER learn?!!!!!) So, problem solved.

---

### Post by Habitual on 2015-08-14
Glad it was something simple.

---

### Post by Greg_Snell on 2015-08-31
Same address bar problem with FF 40.0.3, Lubuntu 14.04 on old Tosh Satellite Pro L10.  gfx.xrender.enable fix no good -- gave me blank FF window if FALSE, or blacked out URL bar if TRUE. Similar with FF 38, but gfx.xrender.enable fix worked

SOLVED by installing FXChrome theme add-on  !!

---

### Post by chris-canberra on 2015-09-25
Yes I had this exact problem, and without much experience I was about to throw Firefox away.

I had previously made the gfx.xrender adjustment previously.

Who do they think should be using Firefox????

---

