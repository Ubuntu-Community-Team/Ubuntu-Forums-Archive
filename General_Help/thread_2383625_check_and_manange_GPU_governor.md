---
title: "check and manange GPU governor"
date: 2018-01-27
forum: General Help
---

### Post by jacopastorius82 on 2018-01-27
Hi all. I was wondering how can i check the gpu governor in use and how can i change it. Really appreciate if it is a gui to manage this.
Thank you!

---

### Post by QIII on 2018-01-27
Hello!

What are you trying to do?  What is the manufacturer and model of your GPU?  What driver are you using?

---

### Post by jacopastorius82 on 2018-01-27
hi, i have nvidia 860M and i'm using proprietary drivers suggested by ubuntu software update. I'd like to set the governor to ondemand, conservative or performance according to my needs. The laptop has its integrated intel vga as well but i'd like to leave it with nvidia all the time and manage the governors

---

### Post by deadflowr on 2018-01-27
You should be able to set the governors in the nvidia settings app which should be installed.
(Open Ubuntu menu (press the super key , or window icon button on your keyboard) and type nvidia, an app should show for nvidia xserver settings, or something similar.)
There should be an option to set the governor in there, maybe; I think it might depend on your card really.

---

### Post by jacopastorius82 on 2018-01-27
thank you deadflowr, i took a look at it and the nvidia server let you choose for adaptive, auto and performance. Not properly a wide range of gov options but better than nothig. Thank you very much!

---

