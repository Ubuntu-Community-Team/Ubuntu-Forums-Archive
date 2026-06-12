---
title: "ubuntu doesn't load login screen"
date: 2008-01-11
forum: General Help
---

### Post by chickmagntwannab on 2008-01-11
Hi I was using my Ubuntu 7.10 desktop like normal the other day and performed a routine update and later decided to restart.  After restarting, GRUB loaded fine and the first splash screen with the orange bar loaded fine but after that it loads a screen with this:
```
*Starting anac(h)ronistic cron anacron
*Starting deferred execution scheduler atd
*Starting periodic command scheduler crond
*Enabling additional executable binary formats binfmt-support
*Checking battery state...
*Running local boot scripts (/etc/rc.local)

```
and then it pops to a black screen with the loading cursor swirling around and pops in and out to the message above after a few minutes it says that the xserver has failed to start for 90 seconds and I should wait a little bit to start x on display 0
I can access the terminal by pressing ctrl+alt+F1 but I am totally at a loss for what to do...please help! 
My computer specs are a Pent. 4 with 4.30 GHz, 1 GB RAM, ATI Radeon X600 video card
any help is much appreciated...thanx!

---

### Post by taurus on 2008-01-11
See if it works after you reconfigure the X server again.  Log in with your username and password, then run

```
sudo dpkg-reconfigure xserver-xorg
```
When done, press <Alt>F7 and then <Ctrl><Alt>Backspace to restart X.

---

### Post by chickmagntwannab on 2008-01-12
well I figured I would uninstall and reinstall the xserver to fix the problem but when I was attempting to reinstall x it said the repositories were not authenticated and would not use them...so now I am stuck without x and am using a Live CD...I am thinking my only hope is to do a clean install unless I can somehow reinstall x from the Live CD

---

### Post by chickmagntwannab on 2008-01-12
I went ahead and reinstalled ubuntu all together and everything is working fine now...thanks for your help

---

