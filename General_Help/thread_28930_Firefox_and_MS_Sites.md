---
title: "Firefox and MS Sites"
date: 2005-04-22
forum: General Help
---

### Post by orion_114 on 2005-04-22
Is there anyway to get firefox to open cetain sites that are "IE only"?
For instance I use firefox as my default browser at work on my windows machine, but I can't open my SUS Admin page with it. It bounces me to a page that says:

> Thank you for your interest in Microsoft Software Update Services

You need to be running a version of Internet Explorer 5.5 or higher in order to use Microsoft Software Update Services.

I would like to dual boot my work laptop with ubuntu, but I need to be able to access certain MS stuff. Are there any other solutions to this problem ?

---

### Post by SGC on 2005-04-22
I think if you change your user agent in firefox, you will be able to foll the site so that it think your are using internet explorer

Just download User agent  switcher extension:
[http://downloads.mozdev.org/useragentswitcher/useragentswitcher.xpi](http://downloads.mozdev.org/useragentswitcher/useragentswitcher.xpi)

and chang your user agent to internet explorer from tool menu

---

### Post by orion_114 on 2005-04-22
Hey SGC,
Well I downloaded it and I managed to open the site. However the page doesn't have all the controls displayed. I cant aprove updates or anythin. :( Are there anymore plugins that can render the controls correctly ?

---

### Post by SGC on 2005-04-22
If SUS is something like windows update , then it uses Activex which will not work on linux as far as i know.

---

### Post by orion_114 on 2005-04-22
Yea SUS is Windows Software Update Services. I need it to rollout patches to the windows hosts. I host the site on my server and access it from my laptop. I wonder if I run wine or some other emulator if I can run IE ? That might solve the problem ? Or will i still have problems with activeX controls ?

---

### Post by LeNain on 2005-04-22
With crossover office you can run IE, there fore i think you can run it under a "simple wine"
 
I didn't try yet

---

