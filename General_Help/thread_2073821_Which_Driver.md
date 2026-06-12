---
title: "Which Driver?"
date: 2012-10-20
forum: General Help
---

### Post by Carterclan on 2012-10-20
My graphic card is an ATI HD Radeon 5430 series

After a fresh 12.10 install the driver in use is 
*X.org X server - AMD/ATI display driver wrapper from xserver-xorg-video-ati (open source ,tested)*

Is it safe for me to install one of the fglrx proprietary drivers as I am reading of all kinds of problems with fglrx in 12.10, though most of what I have read seem to involve older cards than mine.

Thanks in advance

---

### Post by grahammechanical on 2012-10-20
There is only one way to find out.

If we tick to install third party software during the install that usually brings in the proprietary drivers and activates them. Due to Nvidia driver issues causing a broken install whilst testing 12.10, I am now in the habit of activating proprietary drivers after installing.

Regards

---

### Post by Carterclan on 2012-10-20
The proprietary drivers are showing just not sure whether to activate one or not, not sure I have the patience to sort out a black screen after reboot :)

---

### Post by 2F4U on 2012-10-20
As far as I understand it, there are currently problems with the proprietary ATI drivers due to the version of the Xorg server Ubuntu 12.10 uses. If you look through the forum you will find a lot of people reporting problems.

---

### Post by Carterclan on 2012-10-20
Which is why have not yet tried to activate it. Think I will wait for more info to be provided on the situation.
Seems like a lot of people have been caught out by this especially those that upgraded from 12.04 and already had fglrx installed.

---

### Post by Carterclan on 2012-10-20
I'm going to answer my own Question, the answer is NO NO NO stick with the open source driver.
Having decided to give it a try after rebooting was only left with the background, no dash/launcher no top bar no window borders.
Fortunately it was easily remedied as you can still open a terminal with Ctrl,Alt,T.

Just hoping ATI are not going to ignore this and provide us with an updated driver.

---

