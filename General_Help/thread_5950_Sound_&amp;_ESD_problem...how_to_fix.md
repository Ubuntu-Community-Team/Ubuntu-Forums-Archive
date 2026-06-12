---
title: "Sound &amp; ESD problem...how to fix"
date: 2004-11-23
forum: General Help
---

### Post by autek on 2004-11-23
I use Ubuntu for my ham radio apps. I have one that uses the soundcard, line in and line out. However, unless I kill ESD I cannot use the line out for the error that tells me the server is busy. Once I kill ESD the app works fine. I did a search on the forum for an answer, but did not really see anything that helpful. How do I get ESD from loading on boot ?? Is there a decent work-around for this. ?? The app is looking for OSS.

Ed

---

### Post by Magneto on 2004-11-23
[QUOTE=autek]I use Ubuntu for my ham radio apps. I have one that uses the soundcard, line in and line out. However, unless I kill ESD I cannot use the line out for the error that tells me the server is busy. Once I kill ESD the app works fine. I did a search on the forum for an answer, but did not really see anything that helpful. How do I get ESD from loading on boot ?? Is there a decent work-around for this. ?? The app is looking for OSS.

Ed[/QUOTE]
 go to Desktop Preferences ---> Sound  and deselect Enable Sound Server Startup

had problems earlier here

---

### Post by autek on 2004-11-24
Thanks, that was the cure. App works just fine now.
Ed

---

