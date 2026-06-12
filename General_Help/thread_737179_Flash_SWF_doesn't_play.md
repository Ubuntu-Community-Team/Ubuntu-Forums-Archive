---
title: "Flash SWF doesn't play"
date: 2008-03-27
forum: General Help
---

### Post by Black Mage on 2008-03-27
I made an .swf on Windows that plays fine when I use it on windows. But when I transfer it to my Ubuntu Server, it does not play, even when I stick it in html tags. Is there something else I should do?

---

### Post by dcstar on 2008-03-28
> **Black Mage said:**
> I made an .swf on Windows that plays fine when I use it on windows. But when I transfer it to my Ubuntu Server, it does not play, even when I stick it in html tags. Is there something else I should do?

And you have all the flashplayer stuff installed for your browser, don't you?

---

### Post by ibuclaw on 2008-03-28
try enabling the multiverse repository in your sources list.

then
```
 sudo apt-get install flashplugin-nonfree 
```

installs Adobe Flash Player for Mozilla and other socal Web Browsers.

Regards
Iain

---

### Post by ibuclaw on 2008-03-28
Oops, double post.

---

