---
title: "How to start in text mode"
date: 2007-04-11
forum: General Help
---

### Post by kvalis on 2007-04-11
Need to install Nvidia drivers. Tried to open a terminal, and run the install, but get info that Xserver is running and it needs to be shutdown in order to install the Nvidia drivers.

---

### Post by NeoLithium on 2007-04-11
Use CTRL+ALT+BACKSPACE
That should kill the x-server and bring you to a text login screen :)

---

### Post by girishv on 2007-04-11
Hi,

if you are running gdm (most probably by default) killing the X will restart gdm. One easy way of starting a text only is use one of the tty's. You can start it by pressing
ctrl+alt+F1 (F1 to F6 )
Once you are through with your work, logout and press ctrl+alt+F7 to back into your graphical window and restart either by killing gdm (sudo pkill gdm) or ctrl+alt+backspace

Girish

---

### Post by zvacet on 2007-04-11
```
sudo /etc/init.d/gdm stop
```
```
sudo /etc/init.d/gdm start
```

---

### Post by cantormath on 2007-04-11
Yeah,

you got to kill gdm, you cant just ctrl+alt+backspace or ctrl+alt+f1-6 , this doesnt kill gdm.

zvacet  is right........

---

### Post by kvalis on 2007-04-11
That did the trick. Thanks a lot for your suggestions.

Kvalis

---

