---
title: "Ctl+Alt+Backspace doesn't work"
date: 2017-02-19
forum: General Help
---

### Post by tonma on 2017-02-19
I wanted to enable the CTRL+ALT+DEL equivalent of Ubuntu, so I looked up and found this:
[https://askubuntu.com/questions/95192/what-is-the-equivalent-of-control-alt-delete/95202](https://askubuntu.com/questions/95192/what-is-the-equivalent-of-control-alt-delete/95202)

I wrote in my terminal the suggested command:
```
gsettings get org.gnome.desktop.input-sources xkb-options
```

But it still doesn't work, why?
And if that doesn't work, what did the above command do? And should I somehow undo it? (How to?)

Thanks!

---

### Post by howefield on 2017-02-19
Which version of Ubuntu are you using and which desktop environment ?

Ctrl + Alt + Del should bring up the logout/shutdown screen in vanilla Ubuntu.

---

### Post by deadflowr on 2017-02-19
> I wrote in my terminal the suggested command:
```
gsettings get org.gnome.desktop.input-sources xkb-options
```
But it still doesn't work, why?
That command does nothing except show you the current status of the setting.
You want to run this
```
gsettings set org.gnome.desktop.input-sources xkb-options "['terminate:ctrl_alt_bksp']"
```
to change the settings.

---

