---
title: "Upgrade 13.04-&gt;13.10. I can log only as guest."
date: 2014-01-23
forum: General Help
---

### Post by sgasior1 on 2014-01-23
If I try log in window manager = black screen.
If I try log as guest =ok.
How to fix it?

---

### Post by jeanjd63 on 2014-01-23
Hello,
Two ways :
In windows manager, without login :
1) you open a console : CTRL+ALT+F1 you log with your user/password and you do :
[B]df -h
df -i[/B]
and verify there is no value at 100% in column %Use
2) you suppress files .Xauthority .ICEauthority :
**sudo  rm  .Xauthority  .ICEauthority**
3) you do :
[B]sudo  apt-get  update
sudo  apt-get  upgrade[/B]
4) you reboot :
**sudo  reboot**

---

### Post by sgasior1 on 2014-01-23
Unfortunately, no change.
Black screen. But I can log on tty1-6 (ctrl+alt+F1-6)

---

### Post by jeanjd63 on 2014-01-23
On tty1 with your user if you try :
**startx**
what is the result ?

---

### Post by sgasior1 on 2014-01-23
Ok. I will try but I think that is problem with xfce or something. I reboot and try no xfce but icewm. 
Icewm works.

---

### Post by sgasior1 on 2014-01-23
Ok If I try startx on tty1 = black screen
ctrl+alt+F1 and
some errors last lines:

Loading extension GLX 
vesa: Ignore device with a bound kernel driver
The XKEYBOARD keymap compiler (xkbcomp) reports:
warning: Type "ONE_LEVEL" has 1 levels, but <RALT> has 2 symbols
Ignoring extra symbols
Errors from xkbcomp are not fatal to the X server

I give ctrl+C and some:

waiting for X server tho shut down (EE) Server terminated successfully (0). Closing log file.
xinit: unexpected signal 2

---

### Post by jeanjd63 on 2014-01-23
What type of video card have you ?
**sudo  lspci -vnn  |  grep -i  vga**

---

### Post by sgasior1 on 2014-01-23
00:02.0 VGA compatibile controller [0300]: Intel Corporation Mobile 945GM/GMS, 943 /940GML Express Integrated Graphics Controller 
[8086:27a2] (rev 03) (prog-if 00 [Vga controller])

---

### Post by pqwoerituytrueiwoq on 2014-01-23
try this, i had a issue like this when i moved my hdd to a new laptop
```
rm ~/.config/xfce4/xfconf/xfce-perchannel-xml/displays.xml
```
do that from the tty ( CTRL+ALT+F1 )
use CTRL+ALT+F7 to get back to the login screen assuming you are not logged in

---

### Post by sgasior1 on 2014-01-23
It works!
Thank you very much.

---

