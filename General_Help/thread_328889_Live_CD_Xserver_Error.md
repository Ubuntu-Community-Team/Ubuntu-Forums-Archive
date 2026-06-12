---
title: "Live CD Xserver Error"
date: 2006-12-31
forum: General Help
---

### Post by taekwondodogoof on 2006-12-31
Hi,
     I'm trying to run the Live CD to install Ubuntu 6.10. I've tried starting in both regular and safe graphics mode. In both, I get a Xserver error because of server error: no screens found. I'm running a Nvidia GeForce 8800 GTX.

---

### Post by taurus on 2006-12-31
Do you get a console if you press <Ctrl><Alt>F2?

---

### Post by taekwondodogoof on 2006-12-31
Yes, I can get a console. And THanks for the help :D

---

### Post by taurus on 2006-12-31
From the console, run this command to see if it fixes your X problem.

```
sudo dpkg-reconfigure -phigh xserver-xorg
```
Now, press <Alt>F7 to get back to X again.  Do you now see a GUI login screen (make have to press <Ctrl><Alt>Backspace to restart X again)?

---

### Post by taekwondodogoof on 2006-12-31
It brings up a list of resolutions... which one do I pick? Just the one that corresponds to my screen?

---

### Post by taurus on 2006-12-31
I would pick the 1024x768 to be save.  If it doesn't work, run that command again and pick another resolution...  ;)

---

### Post by taekwondodogoof on 2006-12-31
No... it still won't work... I picked 1024x768 and 1920x1200 which is what my monitor supports and it still doesn't work...

---

### Post by taurus on 2006-12-31
I wouldn't go such a high resolution until you have install a driver for your graphic card.  For now, I would stick with a low resolution to be safe!!!

Try the 800x600.

Otherwise, use the alternate CD to install it on your machine then...

---

### Post by taekwondodogoof on 2006-12-31
Ok,since it didn't work I should try the alternate installation CD?
ALso, how come the live CD worked under my GeForce 6800 but not on the 8800? Is it just because it's newer?

---

### Post by taurus on 2006-12-31
Somehow the LiveCD is having a little technical difficulty with your graphic card so it's definitely alternate CD time...

[http://www.gtlib.gatech.edu/pub/ubuntu-releases/edgy/](http://www.gtlib.gatech.edu/pub/ubuntu-releases/edgy/)

---

### Post by taekwondodogoof on 2006-12-31
I got the alternate installation CD burned, and I loaded it, but what option do I use?

---

### Post by taurus on 2006-12-31
First option--to install it!!!

---

