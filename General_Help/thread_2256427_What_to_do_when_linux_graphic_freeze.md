---
title: "What to do when linux graphic freeze?"
date: 2014-12-12
forum: General Help
---

### Post by 915086731 on 2014-12-12
[COLOR=#000000][FONT=Arial]My OS is ubuntu 14.10. Graphic driver is nouveau.
Recently I plugged in an old graphic card which only contains 64M memory but supports dual display. After that my desktop freezes frequently left screen halted, mouse and keyboard no response except sysrq works. I also can login remotely. I try to restart service lightdm to revive my desktop, but the command seems waiting forever given by message "lightdm stop/waiting" . The process Xorg can't be killed. My only solution is reboot by pressing reset button or SysRq magic key. Can anyone help me to revive my desktop without reboot ? Thanks!


[/FONT][/COLOR]

---

### Post by grahammechanical on 2014-12-12
The graphic card is causing the problems. You know that. Since Ubuntu 11.04 was released Ubuntu has needed

> [COLOR=#333333][FONT=Ubuntu]* 3D Acceleration Capable Videocard with at least 256 MB[/FONT][/COLOR]

with that graphic card it matters little how powerful the CPU or how large the amount of RAM. You will need to install Xubuntu or Lubuntu.

> 
[LIST]
[*=left]Graphics card and monitor capable of 800x600 resolution[FONT=inherit][/FONT][FONT=inherit][/FONT]
[*]
[/LIST]
or even another Linux distribution.

[https://help.ubuntu.com/community/Installation/SystemRequirements](https://help.ubuntu.com/community/Installation/SystemRequirements)

You could try installing gnome-session-flashback (search for flashback in the software centre). Then at the login screen you will have two extra login session options - Gnome Flashback (Compiz) and Gnome Flashback (Metacity). The Metacity option might give the best results for that card.

Regards.

---

### Post by 915086731 on 2014-12-13
I am using Xfce all along which is the default desktop environment of Xubuntu. So I think it matters litter about what kind of ubuntu distribution.

---

### Post by 915086731 on 2014-12-13
The system runs smoothly most time. Only except that some times moving mouse to switch application would cause freeze suddenly.

---

### Post by 915086731 on 2014-12-15
[COLOR=#444444][FONT=Arial]I changed my desktop environment to lxde from xfce. Since then the problem disappears. Maybe this issue can be closed[/FONT][/COLOR]

---

### Post by mörgæs on 2014-12-15
You decide. Remember to mark the thread 'solved' when it is.

---

