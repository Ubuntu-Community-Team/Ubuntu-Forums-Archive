---
title: "Screen Turn Off Automatically During Downloading!"
date: 2013-02-19
forum: General Help
---

### Post by Sneakdog on 2013-02-19
The screen will turn off automatically during I try to install new source code on the Ubuntu Software Centre. The machine will stay at the requesting status, download progress bar didn't show the sign of downloading data. After a while (about few minutes), the screen will be switch off and no response, have to pressing the power button the restart it. 

I have to try this few times, but the problem keep repeating. 

I used to download some software from the centre. So I think my network connection is ok.

Someone please help me to solve this issue. Thanks.

---

### Post by dino99 on 2013-02-19
its probably due to the screensaver settings

[http://askubuntu.com/questions/177348/how-do-i-disable-the-screensaver-lock-in-12-04](http://askubuntu.com/questions/177348/how-do-i-disable-the-screensaver-lock-in-12-04)

---

### Post by coldcritter64 on 2013-02-19
Go into system settings, in Unity, the power button far right on the top panel. In the menu that drops down select System Settings there.
Check to see if the screen is set to "Blank", I think the default time may be set at 10 minutes. There are other power saving settings and UI elements here, you can enable or disable the screen lock etc - one I always set to off.

I would set the monitor to "never" turn off (blank) from its current 10 min setting. Alter any other power settings that may cause interference to your usage. Good luck.

---

### Post by fuorviatos on 2013-02-19
Even if it's the screensaver wrong setup, this should be marked as a  critical bug on Launchpad.
For no reason, such thing could bring you to the system hang.
I'd rather check on > /var/log/Xorg.0.log for WW (warnings), EE (errors), just to make sure your video card does not have anything to do with the issue.

---

### Post by Sneakdog on 2013-02-20
I have tested on the machine, is confirm hardware failure. But anyway, thanks for support.

---

### Post by fuorviatos on 2013-02-20
> **Sneakdog said:**
>  is confirm hardware failure. .
How did you come to such conclusion?

---

### Post by Sneakdog on 2013-02-21
> **fuorviatos said:**
> How did you come to such conclusion?

I try to boot into Win 7, it also having the same issue.

---

### Post by fuorviatos on 2013-02-21
> **Sneakdog said:**
> I try to boot into Win 7, it also having the same issue.
OK. I think we can close the topic now.

---

