---
title: "HDMI Extender with Ubuntu has Colour Problem - Other OS works fine"
date: 2023-08-11
forum: General Help
---

### Post by timbergetter2 on 2023-08-11
I have installed a Mini HDMI Cat5e/6 Extender (Digitech AC-1726) onto my Ubuntu 22.04 LTS system to allow a second monitor to be operated in the next room. Everything is working except that there is now a very pronounced colour cast (magenta) on the second monitor. This colour cast is not present when a HDMI cable is used instead of the extender ethernet cable. I get the same problem if I use another Ubuntu computer or if I swap the monitors around or if I use other ethernet cables. Using just one monitor with the extender also causes the problem.

 To troubleshoot this problem further I installed Windows 11 on the computer and the colour cast disappears and extender seems to work perfectly. I then installed Pop!_OS (an Ubuntu derivative) on to the computer and again, the colour cast disappears and extender seems to work perfectly.

 I even tried a third instance of Ubuntu residing on a USB thumb drive and again I get the colour cast when I use the extender. What could there be about Ubuntu that causes the colour cast when an extender is used, but when Windows 11 or Pop!_OS is used there is no problem?

---

### Post by timbergetter2 on 2023-08-13
I have also posted this question here [https://askubuntu.com/questions/1481987/hdmi-extender-with-ubuntu-has-colour-problem-other-os-works-fine](https://askubuntu.com/questions/1481987/hdmi-extender-with-ubuntu-has-colour-problem-other-os-works-fine) and further discussion is evolving there.  If you would like to comment, would you kindly do that on the AskUbuntu forum.

---

### Post by HermanAB on 2023-08-13
There is a serial line protocol running over HDMI between the computer and the screen to configure things.  With bad cables, things can go wrong.  You can try to reset it with xrandr - assuming that you are using X.

---

