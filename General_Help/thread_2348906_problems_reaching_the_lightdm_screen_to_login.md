---
title: "problems reaching the lightdm screen to login"
date: 2017-01-09
forum: General Help
---

### Post by Neill_R on 2017-01-09
Hello

I am in seroius need of some help and guidance to enable me to get back into my machine in GUI mode. I am able to Ctrl-Alt-F1 and log in to a character screen. 

**Background**

This machine is an HP G61 laptop and is my main working machine however I do do trials on it to. The machine has Ubuntu 14.04 server and Lubuntu-desktop installed over the top.
I recently tried to install centrifydc so as to join a windows domain however this went wrong and I uninstalled centrifydc. On reboot I do not get the lightdm screen login.

I am hoping to find a solution THAT DOES NOT INVOLVE a RE-INSTALL

Also asking in [http://community.centrify.com/t5/Centrify-Express/problems-reaching-the-lightdm-screen-to-login/td-p/26444](http://community.centrify.com/t5/Centrify-Express/problems-reaching-the-lightdm-screen-to-login/td-p/26444)

---

### Post by townview123 on 2017-01-17
Is this a problem that cannot be resolved by manually starting the GUI?

---

### Post by deadflowr on 2017-01-17
> **townview123 said:**
> Is this a problem that cannot be resolved by manually starting the GUI?

Maybe, maybe not

You can, or can try to,log into an lxde session with
```
startlxde
```
from that screen in ctrl+alt+F1


But about the lightdm situation, first check to see that it's properly installed
```
dpkg -l | grep lightdm
```
and if it seems to be try to reconfigure it with
```
sudo dpkg-reconfigure lightdm
```
then try to restart lightdm, or even better reboot completely.

But a reboot would be up to you, since this is also a server.

---

