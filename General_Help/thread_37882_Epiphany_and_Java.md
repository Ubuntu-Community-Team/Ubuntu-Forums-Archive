---
title: "Epiphany and Java"
date: 2005-05-29
forum: General Help
---

### Post by larry on 2005-05-29
Hi Everybody,
I have been experiencing problems with Java applets while web surfing for quite a while.
Sometimes my browsers (no matter if I use epiphany or galeon or firefox) simply freeze or cannot run the java applets.
I tried installing gcjwebplugin, but it does not help that much as the browsers often crash (I already sent a bug report).
Any advice about how to fix the problem? I have installed flashplayer-mozilla, which helped me with many websites, but the mentioned problems are persisting.
Thanks for your help.
Larry

---

### Post by arnieboy on 2005-05-29
from terminal do a :
sudo apt-get install sun-j2re1.5
Restart firefox.
-arnieboy

---

### Post by larry on 2005-05-30
Thanks for your help, but where can I find it? I am currently using both the universe and multiverse repositories, but apt-cache cannot get it.
Cheers
Larry

---

### Post by arnieboy on 2005-05-30
Its in ubuntuforums backports. search for "backports" on ubuntuforums and u will know what to add in the apt config file.

---

### Post by larry on 2005-06-01
Done! Now Epiphany is alright.
Cheers
Larry

---

