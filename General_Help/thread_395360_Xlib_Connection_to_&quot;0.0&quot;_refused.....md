---
title: "Xlib: Connection to &quot;:0.0&quot; refused...."
date: 2007-03-28
forum: General Help
---

### Post by spankymasterc on 2007-03-28
Well at first i was getting and error of GDM not having enough space or what not but now when i go and log in it works but then it just starts as a black screen and does absolutely nothing so i figure to Crtl + Alt + Backspace then Ctrl + Alt + F1 and log in there and use command startx and i get this 
```

Xlib:Connection to ":0.0" was refused by server
Xlib:Invalid MIT-MAGIC-COOKIE-1 Key
giving up
Xinit:unable to connect to x server
Xinit: No such process (errno3): server error

```

Well now i dont know what to do and i dont want to reformat hd because i have so much apps and i customized it alot.....

Well hope someone can help thx in advance :guitar:

---

### Post by ndefontenay on 2007-03-28
Do you got some backup of your xorg.conf?

Do this:

```
cd /etc/X11
```

You will see something like this in there.

Below is my X11 folder (I should clean it by the way)

```
app-defaults             xorg.conf.20070213195902       xorg.conf_backup_200703082248
cursors                  xorg.conf.20070213195958       xorg.conf_backup_manual
default-display-manager  xorg.conf.20070213200259       Xresources
fonts                    xorg.conf.20070213200403       Xsession
rgb.txt                  xorg.conf.20070213200608       Xsession.d
X                        xorg.conf.backup               Xsession.options
xinit                    xorg.conf_backup_200702120744  XvMCConfig
xkb                      xorg.conf_backup_200702132001  Xwrapper.config
xorg.conf                xorg.conf_backup_200702230809
```


everytime there's a change you should get a backup of your xorg.conf file. Try to locate one with a date before your problem occured and replace the current xorg.conf with a backed up one.

---

