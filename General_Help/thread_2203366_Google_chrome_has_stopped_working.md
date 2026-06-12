---
title: "Google chrome has stopped working"
date: 2014-02-03
forum: General Help
---

### Post by Ruudv23 on 2014-02-03
Ubuntu 13.10 Gnome
Google Chrome Versión 32.0.1700.102

My Google chrome has stopped working (it goes in to a state of not responding)

Terminal shows this:

desktop:~$ google-chrome
[5015:5045:0203/014708:ERROR:nss_util.cc(558)] After loading Root Certs, loaded==false: NSS error code: -8018
--2014-02-03 01:48:08--  [https://clients2.google.com/cr/report](https://clients2.google.com/cr/report)
Resolviendo clients2.google.com (clients2.google.com)... 74.125.227.238, 74.125.227.228, 74.125.227.227, ...
Conectando con clients2.google.com (clients2.google.com)[74.125.227.238]:443... conectado.
Petición HTTP enviada, esperando respuesta... Violación de segmento. (waiting response... Segment Violation)

---

### Post by PotatoHead007 on 2014-02-03
hmm, you mean you downloaded chrome from the website? I use the chromium-browser, never had any problems.
I think it works better, you can try it:
```
sudo apt-get install chromium-browser
```

---

### Post by ajgreeny on 2014-02-03
Try a new profile/user for chrome as yours may be corrupt.  I have no idea how you do that in chrome, but you should be able to find out easily enough.  For chromium the configuration files are at ~/.config/chromium, so chrome may also put its files somewhere in ~/.config

---

### Post by Buntu Bunny on 2014-02-04
An update for chrome was available this morning in update manager. Has that helped?

---

