---
title: "Resolution problem"
date: 2007-10-11
forum: General Help
---

### Post by f0rt on 2007-10-11
Hello,

This is my first time on a Linuxish system, and I'm having problems with my resolution. I installed Ubuntu yesturday, and I can't make my resolution any larger than 800x600. I know it's not my video card, because it previously ran Windows XP at 1024x768 with no problems. 

Thanks in advance.

---

### Post by taurus on 2007-10-11
What video card do you have?  You probably need to install a driver for it before you can go to higher resolutions.

Try to reconfigure it again with

Applications -> Accessories -> Terminal
```
sudo dpkg-reconfigure --phigh xserver-xorg
```
When done, press <Ctrl><Alt>Backspace to restart X again.

---

