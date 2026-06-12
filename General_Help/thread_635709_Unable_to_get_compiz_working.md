---
title: "Unable to get compiz working"
date: 2007-12-09
forum: General Help
---

### Post by Atow on 2007-12-09
Ok i have a Compaq laptop, 1gb ram, 8gb partition for ubuntu dual booted. Loaded up Gutsy gibbon 7.10, my ati is integrated 200m.

Compiz is installed, composite option is turned on in Xorg.conf, Anytime i turn GL desktop on, it doesnt save, and nothing of compiz works. It worked a while back in xubuntu with fiesty fawn but it broke after some updates.  

Ideas? questions? concerns?

---

### Post by thebee12 on 2007-12-09
have u installed all the latest packages related to compiz such as the settings manager?

---

### Post by Atow on 2007-12-09
yeah and everything is turned on, but isnt working, the rotating cube, water, reflection, etc. thats all set to on and that part is saving but nothing is activating

---

### Post by thebee12 on 2007-12-09
it may seem like a dumb question but did u restart after making changes in the settings-manager and make sure that visual effects in the Appearance dialog box are set to custom

---

### Post by Atow on 2007-12-09
every time i try it wont let me: desktop effects could not be enabled

---

### Post by Sjovan on 2007-12-09
[the home page for compiz got some good documentation]("http://compiz.org/Documentation/Documentation")

[the FAQ isn't bad either. It helped me alot]("http://compiz.org/FAQ/Users")

---

### Post by tenchu77491 on 2007-12-09
Hmm, the general method I use is this,

1. use restricted driver
2. install compiz
3. change composite to "1" or "enable" in xorg.conf
4. sudo apt-get install xorg-driver-fglrx
5. restart your computer
6. click on enable desktop effects

---

### Post by Sjovan on 2007-12-09
well if you got the drivers, maby you should reconfigure xorg and play around with the settings on this url [http://compiz.org/ATI](http://compiz.org/ATI)

---

