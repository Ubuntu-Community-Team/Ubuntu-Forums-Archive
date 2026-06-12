---
title: "Xubuntu 18.04.3 - cannot restore system after display enters power saving mode"
date: 2019-09-22
forum: General Help
---

### Post by marcusadamski on 2019-09-22
Hello,

I've just moved from Lubuntu to Xubuntu, and now encountering a power saving issue. I've turned the power saving mode on my monitor off, so the desktop is the controlling system. My monitor is a Benq GW2760S, I'm using HDMI to connect. The monitor is configured to use HDMI as the input.

After my monitor screen goes black, the monitor indicator turns from green to amber. From that point I cannot revive the system - no amount of keyboard pressing nor mouse movement will wake the monitor. If I disconnect the monitor power, it restarts with "no cable connected". I never has this issue with my older Xubuntu Mint, nor the recent 19.04 Lubuntu.

Can anyone suggest a solution, because I'm having to hard reboot my system every time my system enters power saving mode - which will eventually cause file system problems.

Many thanks for any help,
Marc

---

### Post by Skaperen on 2019-09-23
is it running on battery or plugged in?

---

### Post by mörgæs on 2019-09-23
How does Xubuntu 19.04 work?

---

### Post by him610 on 2019-09-24
Re: Xfce Power Manager under setting Display 
How is the Display power management control set?
Blank after ?
Put to sleep after ?
Switch off after ?

---

### Post by uRock on 2019-09-24
I had this problem as well. I ended up turning off the power saving mode, which I normally do soon after an install.

---

### Post by marcusadamski on 2019-09-25
Thanks for the replies. To respond to a few of the questions:

- my system is a desktop, so no battery
- haven't tried Xubuntu 19.04
- regarding the display power manager, it's currently set to 'never' for everything to avoid any issues. However, I did experiment with just blank after = 2 mins, put to sleep after = never and switch off after = never ... which resulted in the monitor going blank after 2 mins as promised, but was then unable to restore to a working display. Had to restart again...

So simply power saving the monitor to blank will cause the issue. Seems like either Xubuntu is not signaling the monitor to awake, or the monitor is ignoring the signal. However, I had no issues with the previous install of Lubuntu.

Thanks in advance

---

### Post by mörgæs on 2019-09-25
> **marcusadamski said:**
> 
- haven't tried Xubuntu 19.04


If you have found that Lubuntu 19.04 works then it's worth a try.

---

### Post by marcusadamski on 2019-10-01
Update - also if I "lock screen", the screen instantly goes black, and again - no matter how much mouse or keyboard movement, the display will not respond. Again, only solution is to restart the machine.

Out of necessity, I had to stop  (1) of the display from blanking and also (2) from locking screen -  to avoid this issue - but this leaves my machine very vulnerable.

Surely someone has a suggestion / seen this before?


Any help is greatly appreciated

---

