---
title: "Logon Screen Doesn't Load...."
date: 2007-11-23
forum: General Help
---

### Post by ntowakbh on 2007-11-23
I use Ubuntu 7.10, Gusty Gibbon.  At the moment, I am glad that I have a dual boot system, because I can ask for help, by booting into Windows XP.  This morning, I turned on my computer, selected Ubuntu 7.10, from the list, and waited, when it is at the part where the log on screen loads, the mouse turns into the little loading wheel, the screen flashes, and it does this again.  It is like a continuous loop.  Can someone please help me?  The only other alternative I currently see, is reinstalling Ubuntu via live CD, if possible, I do not want to resort to this, as I would loose all software that I've installed, all my files, and my customizations. 

Please, any help would be appreciated.

---

### Post by taurus on 2007-11-23
Go to a console by <Ctrl><Alt>F2.  Log in with your username and password.  Then, reconfigure X again with

```
sudo dpkg-reconfigure -phigh xserver-xorg
```
When you are done, go back to that GUI login screen with <Alt>F7 and restart X with <Ctrl><Alt>Backspace.

---

### Post by ntowakbh on 2007-11-23
> **taurus said:**
> Go to a console by <Ctrl><Alt>F2.  Log in with your username and password.  Then, reconfigure X again with

```
sudo dpkg-reconfigure -phigh xserver-xorg
```
When you are done, go back to that GUI login screen with <Alt>F7 and restart X with <Ctrl><Alt>Backspace.

Thanks, I'll give it a try.

---

### Post by ntowakbh on 2007-11-23
Nope, didn't work.

---

### Post by taurus on 2007-11-23
Have you even tried rebooting the machine after you reconfigured your X server with that command?

---

