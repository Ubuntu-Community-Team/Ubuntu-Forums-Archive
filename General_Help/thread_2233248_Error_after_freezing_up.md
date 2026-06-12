---
title: "Error after freezing up"
date: 2014-07-07
forum: General Help
---

### Post by kakashi_12 on 2014-07-07
I just got done installing Wine from Software Center. The Software Center screen froze after awhile because I was switching between users doing other things while waiting for Wine to install.
I had to Log Out and back in to get the screen back. Wine continued to install, then finished. I got this error (see attachment). Not sure if it's an error because of Wine or because I had to force log out and back in. Looks like Wine installed correctly.

---

### Post by ubudog on 2014-07-07
I would try reinstalling ttf-mscorefonts-installer.

```
sudo apt-get remove ttf-mscorefonts-installer
```
```
sudo apt-get install ttf-mscorefonts-installer
```

---

### Post by kakashi_12 on 2014-07-07
Ok. Thanks. I've already rebooted several times and haven't seen the error since. How do I know if it's cleared or not?

---

### Post by ubudog on 2014-07-07
You should be good now, as long as you didn't get any errors when reinstalling ttf-mscorefonts-installer.  :)

---

