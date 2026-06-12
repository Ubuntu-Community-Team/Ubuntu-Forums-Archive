---
title: "Unity doesn't load, no Launcher, no Dash appears"
date: 2014-11-18
forum: General Help
---

### Post by Lingadharini_Viswa on 2014-11-18
I tried upgrading my ubuntu 14.04 to ubuntu 14.10. But I encountered some errors and everything was reset. I tried this twice or thrice.
I didnt know if i pressed any keys in frustration, my screen went blank. Only desktop appears, the icons on the desktop and the mouse.[IMG]http://i.stack.imgur.com/9JClV.png[/IMG]



Nothing else appears. I cant find the dash menu, top panels, etc. The entire screen went blank. I tried googling. Some people have recommended resetting unity and reinstalling unity-desktop from tty by pressing ctrl+f2.
I have tried that. But it didnt work. Also, i cant use any shortcuts like Ctrl+Alt+T for launching terminal.

Kindly help me.
Thank You.

---

### Post by Lingadharini_Viswa on 2014-11-21
Should I reinstall all the ubuntu again?

---

### Post by flaymond on 2014-11-21
If you can't open the Terminal, than I highly suggest you to reinstall Ubuntu back or if doesn't worked...reinstall the the 14.04 version......

---

### Post by Lingadharini_Viswa on 2014-12-08
Thank you. I m going to reinstall ubuntu. thanks. :)

---

### Post by Lingadharini_Viswa on 2014-12-08
My laptop is a dual boot machine. I have installed windows 8.1 and ubuntu. Is it possible to open ubuntu and run the ubuntu installation files from there..? If so, how to open the drive from command line if I plug in my removable disk..?

---

### Post by CantankRus on 2014-12-08
No need to reinstall.
Boot up in [**_[COLOR="#B22222"]recovery mode[/COLOR]_**]("https://wiki.ubuntu.com/RecoveryMode").
Select the  "drop to root shell" option and mount / in read write mode...
```
mount -o rw,remount /
```

then enable networking with...
```
dhclient [COLOR="#FF0000"]eth0[/COLOR]
```
use [COLOR="#FF0000"]wlan0[/COLOR] for wireless.

Now you can install **gnome-session-flashback** to give you a functional desktop where you can repair unity from.
```
sudo apt-get install gnome-session-flashback
```

When finished installing type in **exit** and press enter.
Resume normal boot and at the greeter choose the **Gnome Flashback Metacity** session.
Within this session open a terminal and run....
```
dconf reset -f /org/compiz/
```
Log out and log back in to the **Ubuntu** session.
Hopefully unity dash and panel will be showing. [-o<

---

