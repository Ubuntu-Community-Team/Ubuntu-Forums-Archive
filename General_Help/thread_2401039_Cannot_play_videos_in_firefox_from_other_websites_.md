---
title: "Cannot play videos in firefox from other websites except youtube"
date: 2018-09-12
forum: General Help
---

### Post by angel-cake on 2018-09-12
Hello, as the title states, i cannot play videos in firefox from other websites, but i CAN play youtube videos. I try everything, like disabling extensions and plugins, disabling the hardware acceleration but nothing seems to work. I have ubuntu 18.04 (bionic) and firefox 62.0. 
it's worth noting that i had to reistall linux on my laptop because there were some issues that would not let me use it, but before those issues appered i could play videos normally outside youtube.
Please help.

---

### Post by DuckHook on 2018-09-12
Youtube uses HTML5 which is native to your browser whereas some of your other websites may be using other codecs. Have you installed *ubuntu-restricted-extras*?

---

### Post by angel-cake on 2018-09-12
no, i haven't @DuckHook
Also, sorry for the typos.

---

### Post by DuckHook on 2018-09-12
> **angel-cake said:**
> …sorry for the typos.
No apologies needed. Many forum members are posting from handhelds these days.
```
sudo apt install ubuntu-restricted-extras
```
Let us know if that helps for at least some sites.

Being part of FOSS Linux, Ubuntu does not ship with proprietary codecs, so you must install them yourself. There are others besides the collection above, but let's try that one first. Many sites use such proprietary codecs. You may have to do a little digging to see which codecs your sites use.

A word to the wise—oddball codecs are a known vector for malware, so it pays to be on guard.

---

### Post by angel-cake on 2018-09-12
yessss, it workeddd!!!, thank you very much :-)

---

### Post by Dennis N on 2018-09-12
To play some video (flash content for example) you need to authorize playback for the web page containing the content.

Right click on the page itself, select "view page info", then open the Permissions tab (top).
To enable flash player, scroll down to "Run Adobe Flash", uncheck "Use Default" and check "Allow". Reload the page.
Of course, for flash you also must have the adobe flash player installed as well.

---

### Post by angel-cake on 2018-09-12
thanks for the infromation @Dennis N

---

