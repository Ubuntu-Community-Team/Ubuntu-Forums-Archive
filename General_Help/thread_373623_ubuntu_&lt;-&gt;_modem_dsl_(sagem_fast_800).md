---
title: "ubuntu &lt;-&gt; modem dsl (sagem fast 800)"
date: 2007-03-01
forum: General Help
---

### Post by VBMAN on 2007-03-01
i have a modem dsl (sagem fast 800) and i want connect to the internet by UBUNTU....what can i do;;;;;;i need any codec or anything else.....
please help...thank u....:) :) :) :)

---

### Post by Stemp on 2007-03-01
Here : [http://ubuntuforums.org/showthread.php?t=189363](http://ubuntuforums.org/showthread.php?t=189363) ?

---

### Post by zvacet on 2007-03-01
Go to the system>administration>network setting and click on it.You will see window and your modem if it is recognized by Ubuntu.Highlight your modem and press properties.that will ope other window in witch you will choose type of your connection(dhcp,static)and chekthe box in upper left make this connection aveilable(or something like that).Close.Go to the terminal and type```
sudo pppoeconf
```
and just answer the questions.If have problem with connection type in terminal pon dsl-provider.To avoid that I recomend you to look this
[http://ubuntuforums.org/showthread.php?t=239815&highlight=rp-pppoe]("http://ubuntuforums.org/showthread.php?t=239815&highlight=rp-pppoe")
I hope it helped.

---

### Post by VBMAN on 2007-03-01
> **zvacet said:**
> Go to the system>administration>network setting and click on it.You will see window and your modem if it is recognized by Ubuntu.Highlight your modem and press properties.that will ope other window in witch you will choose type of your connection(dhcp,static)and chekthe box in upper left make this connection aveilable(or something like that).Close.Go to the terminal and type```
sudo pppoeconf
```
and just answer the questions.If have problem with connection type in terminal pon dsl-provider.To avoid that I recomend you to look this
[http://ubuntuforums.org/showthread.php?t=239815&highlight=rp-pppoe]("http://ubuntuforums.org/showthread.php?t=239815&highlight=rp-pppoe")
I hope it helped.
thank you guys,,,,,,:guitar: :guitar: :guitar:

---

