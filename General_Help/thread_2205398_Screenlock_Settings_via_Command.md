---
title: "Screenlock Settings via Command"
date: 2014-02-13
forum: General Help
---

### Post by vendethiel on 2014-02-13
Is there anyway to set screen lock settings for unity via terminal?

[http://askubuntu.com/questions/70124/how-to-prevent-screensaver-from-locking-the-screen-in-unity](http://askubuntu.com/questions/70124/how-to-prevent-screensaver-from-locking-the-screen-in-unity)

-v

---

### Post by rburkartjo on 2014-02-13
try crtl+alt l(thats L not i)

---

### Post by rburkartjo on 2014-02-13
my bad i gave you the shortcut keys to lock the desktop in lubuntu 13.10 and they wont work on unity. dont know any way to lock from the terminal.

---

### Post by vendethiel on 2014-02-19
> **rburkartjo said:**
> my bad i gave you the shortcut keys to lock the desktop in lubuntu 13.10 and they wont work on unity. dont know any way to lock from the terminal.

Thanks, unfortunately that's not what i'm looking for. I'm looking to configure the screen lock settings via the terminal. I'm writing a bash script that will configure specific security settings for Ubuntu 12.04 clients and can't seem to figure out how to configure this without using the gui.

---

### Post by Toz on 2014-02-19
You can use the gsettings command. [Examples]("http://askubuntu.com/questions/109120/how-do-i-turn-off-the-screen-saver-using-the-command-line"):
```
gsettings set org.gnome.desktop.screensaver lock-delay 3600
gsettings set org.gnome.desktop.screensaver lock-enabled false
gsettings set org.gnome.desktop.screensaver idle-activation-enabled false
```
A list of available keys can be found via the gui tool "dconf-editor".

---

