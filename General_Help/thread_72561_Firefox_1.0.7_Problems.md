---
title: "Firefox 1.0.7 Problems"
date: 2005-10-06
forum: General Help
---

### Post by Julian_Kolm on 2005-10-06
I am using an fully updated ubuntu with activated backports

I had the same Problems as described in the apt-get/firefox thread and solved them in almost the same way as described 

since the when I try to enter the following Webpage 
[http://webct.univie.ac.at/webct/urw/lc3327112.tp3415954/logout.dowebct?insId=20881&insName=Universit%ef%bf%bdt%20Wien&glcid=131.130.1.204-1081937175801-2002043001](http://webct.univie.ac.at/webct/urw/lc3327112.tp3415954/logout.dowebct?insId=20881&insName=Universit%ef%bf%bdt%20Wien&glcid=131.130.1.204-1081937175801-2002043001)
firefox breaks down, wich means that it simply stops working.
(I am sorry that I can't publish the pwd but the content is rahter sensitive)

This wouldn't be to uncommon but strangely it works when I start firefox from a root terminal

when checked the "Systemüberwachung" after firefox has broken down I could see that the sub process of firefox vm-java was sleeping

thank you for your help

---

### Post by aysiu on 2005-10-09
Things are a bit complicated with you using root and all, but if Firefox does one thing with one user and another thing with another user, sometimes it's because one of the user profiles has become corrupt somehow. Have you tried backing up your /home/username/.mozilla file, deleting the original, then restarting Firefox?

---

