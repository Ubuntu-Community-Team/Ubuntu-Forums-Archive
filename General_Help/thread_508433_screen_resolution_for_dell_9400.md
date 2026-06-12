---
title: "screen resolution for dell 9400"
date: 2007-07-24
forum: General Help
---

### Post by aum11 on 2007-07-24
Have been trying to resolve this issue for a couple of days and cannot fix it by following previous posts.
Have recently installed feisty on a new 9400.  It has the ATI x1400 for a 17"uxga with 1920x900.

Have downloaded the latest ATI driver and updated /etc/X11/xorg.conf .

However, when checking screen preferences via system/preferences it still only gives a max of 1024x768.

Your expert help is much needed and appreciated.  Ta

---

### Post by bigken on 2007-07-24
try this sudo dpkg-reconfigure -phigh xserver-xorg use the space bar to select your resolutions

---

### Post by aum11 on 2007-07-24
Thanks bigken for your quick reply.

Did as You suggested, however 1920x1200 causes the system to freeze on reboot.  Tried 1440x900 also but the system simply ignores this and returns to 1024x768 on rebooting.

@ questions remain...why can't 1920x1200 be handled(certainly can under windows)

...and why is 1440x900 ignored?

Thanks

---

### Post by bigken on 2007-07-24
ok try this sudo dpkg-reconfigure xserver-xorg and select ati as your driver

---

### Post by aum11 on 2007-07-24
Selecting ATI simply caused reboot to fail with "failed to start x server"

So i reset it back to fglrx and tried a lesser resolution of 1680x1050.  It rebooted at 1280x1024 with other lower resolution options...it defies belief.

Any more thoughts?

---

### Post by bigken on 2007-07-24
have you tried [FONT=Verdana][SIZE=2]1920 x 1200[/SIZE][/FONT]

---

### Post by bigken on 2007-07-24
wuxga supports upto 1920x1200 but uxga will only support 1440x900

---

### Post by aum11 on 2007-07-24
Thanks for Your help bigken.

Yes have tried 1920x1200 and also 1680x1050 and 1400x1050.  All cause the system to hang.

The highest that will work is 1280x1024....at least this is better than the previous 1024x768...but this can run at 1920x1200!  Refresh rate is 60hz.

Only resolutions 1280 and below show up.

---

### Post by bigken on 2007-07-24
try 1440x900

---

### Post by aum11 on 2007-07-24
1400x900 also does not show up.  The highest is 1280x1024.

Is it possibly the refresh rate?

I am bamboozled

---

### Post by bigken on 2007-07-24
no I think its the fglrx driver sorry cant assist anymore :(

---

### Post by aum11 on 2007-07-24
Good night and thanks from Australia

---

### Post by yorkie on 2007-07-24
Possible fix is here
[http://xoomer.alice.it/sam_psy/soft/ubuntu_install.html](http://xoomer.alice.it/sam_psy/soft/ubuntu_install.html).
good luck

---

### Post by strabes on 2007-07-24
Did you follow this how-to? [https://help.ubuntu.com/community/BinaryDriverHowto/ATI#head-d8c6fd05bce340dfc3ad483abf0e18997868540b](https://help.ubuntu.com/community/BinaryDriverHowto/ATI#head-d8c6fd05bce340dfc3ad483abf0e18997868540b)

---

### Post by aum11 on 2007-07-27
Thanks guys but neither of these worked.

I am beginning to think that noone has got 1920x1200 working on a dell 9400 with ATI  x1400.

Please prove me wrong!!!  This resolution of 1280x1024 is awful.

---

### Post by strabes on 2007-07-28
I have the E1705 which is the same as the 9400, and the X1400 card. You have to install fglrx, run aticonfig --initial and restart the x server. The native resolution of the screen should be automatically detected. Have you tried running ```
sudo dpkg-reconfigure xserver-xorg
```

You absolutely must use the fglrx driver. There is no way around it with the x1400 card. I don't think it's that bad except for its lack of composite support, which is a big negative.

---

### Post by aum11 on 2007-07-28
I have tried it many times!!

can you get 1920x1200 resolution?  I have the uxga screen.

---

### Post by dcstar on 2007-07-28
> **aum11 said:**
> Thanks for Your help bigken.

Yes have tried 1920x1200 and also 1680x1050 and 1400x1050.  All cause the system to hang.
........

Getting a blank screen is not the system "hanging", it can be just a bad refresh rate for the resolution.

---

### Post by aum11 on 2007-07-28
It is currently at 60hz refresh rate...should it be something different?

---

### Post by aum11 on 2007-08-02
Finally I was able to achieve the 1920x1200 screen resolution but had to reinstall but without using the separate /home partition brought over from a dell 9300.

I have no idea why the configuration should get corrupted by a /home from another computer, but it did...many times!

I am entering this in order to help other 9400 users.  I ended up installing from the alternate install cd  which went smoothly.  You will need the following workaround (gathered from other posts) when X fails on boot:

sudo apt-get install xorg-driver-fglrx
sudo nano /etc/X11/xorg.conf 

Under "device" change "vesa" to "fglrx"  , then cntl-x to save

sudo /etc/init.d/gdm restart

---

