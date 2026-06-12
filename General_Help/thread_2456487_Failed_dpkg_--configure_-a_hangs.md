---
title: "Failed dpkg --configure -a hangs"
date: 2021-01-12
forum: General Help
---

### Post by ionmich1 on 2021-01-12
Version 20.04
```
$ sudo dpkg --configure -a
Setting up pepperflashplugin-nonfree (1.8.6ubuntu1) ...
--2021-01-12 10:48:48--  https://get.adobe.com/flashplayer/webservices/json/?platform_type=Linux&platform_arch=x86_64&browser_dist=Chrome
Resolving get.adobe.com (get.adobe.com)... 193.104.215.66
Connecting to get.adobe.com (get.adobe.com)|193.104.215.66|:443... connected.
HTTP request sent, awaiting response... 302 Found
Location: https://www.adobe.com/products/flashplayer/end-of-life.html?platform_type=Linux&platform_arch=x86_64&browser_dist=Chrome [following]
--2021-01-12 10:48:49--  https://www.adobe.com/products/flashplayer/end-of-life.html?platform_type=Linux&platform_arch=x86_64&browser_dist=Chrome
Resolving www.adobe.com (www.adobe.com)... 2600:141c:8::bdf7:a318, 2600:141c:8::bdf7:a311, 189.247.202.168, ...
Connecting to www.adobe.com (www.adobe.com)|2600:141c:8::bdf7:a318|:443... connected.
HTTP request sent, awaiting response... 
```

Never completes. Any suggestions will be appreciated.

---

### Post by deadflowr on 2021-01-12
Flash is dead.
Not surprising it fails to download.

Edit: See :[https://www.adobe.com/products/flashplayer/end-of-life.html]("https://www.adobe.com/products/flashplayer/end-of-life.html")

---

### Post by ionmich1 on 2021-01-12
> **deadflowr said:**
> Flash is dead.
Not surprising it fails to download.

Edit: See :[https://www.adobe.com/products/flashplayer/end-of-life.html](https://www.adobe.com/products/flashplayer/end-of-life.html)

So how do I ```
 dpkg --configure -a 
``` now?

---

### Post by deadflowr on 2021-01-12
Try running
```
sudo apt purge pepperflashplugin-nonfree
```
Post results

---

### Post by ionmich1 on 2021-01-12
> **deadflowr said:**
> Try running
```
sudo apt purge pepperflashplugin-nonfree
```
Post results

It worked just fine. Many thanks. I learned something new.

---

