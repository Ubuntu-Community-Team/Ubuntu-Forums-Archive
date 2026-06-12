---
title: "Theming Root Apps"
date: 2008-06-04
forum: General Help
---

### Post by Exsecrabilus on 2008-06-04
[Here](http://tombuntu.com/index.php/2007/09/18/theme-applications-running-as-root-in-ubuntu/), it says I should run this command to change the root theme to my custom theme:

```
sudo ln -s ~/.themes /root/.themes
sudo ln -s ~/.icons /root/.icons
sudo ln -s ~/.fonts /root/.fonts
```
But another source, such as [this](http://ubuntuforums.org/showthread.php?t=148325), says to do this:

```
sudo rm -R /root/.themes
sudo rm -R /root/.icons
sudo ln -s /home/$USER/.themes /root
sudo ln -s /home/$USER/.icons /root
```
Which one do I use to change the root theme?

---

### Post by aysiu on 2008-06-04
I'd go with the first set of instructions. But to be safe, I'd mix and match: ```
sudo rm -r /root/.themes
sudo rm -r /root/.icons
sudo ln -s ~/.themes /root/.themes
sudo ln -s ~/.icons /root/.icons
sudo ln -s ~/.fonts /root/.fonts
``` When you do those *sudo rm -r* commands, be sure to *paste* them in instead of *retyping* them. Otherwise, they can be dangerous.

---

