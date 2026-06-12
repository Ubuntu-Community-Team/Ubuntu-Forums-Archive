---
title: "Any way to boot in to terminal but still have GUI available?"
date: 2012-12-23
forum: General Help
---

### Post by arrjayjee on 2012-12-23
Basically I want to know if I can boot directly in to a gnome terminal, and then if I type in to terminal "gedit", the text editing window window will pop up. Or if I type in "google-chrome", the web browser will open, but the desktop will itself just be a terminal. No task bar or anything.

Is this possible?

---

### Post by Cookieh on 2012-12-23
I believe its possible, as when you boot into an Ubuntu, many different terminals load. They are reached by the function keys (F1,F2, F3...) where F1 is the GUI mode, and others are terminals. I only know this but I dont know how to enter them.

---

### Post by sudodus on 2012-12-23
You can boot into a text screen, if you change a boot option, and from the text screen you can easily start an X-window graphical desktop environment. But you cannot run graphical applications without a graphical desktop environment. If you have several screens, they can be run in different modes.

An alternative is to run the primitive openbox session without a desktop environment such as LXDE or XFCE.

Change a line in [FONT="Courier New"]/etc/default/grub[/FONT] to
```

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash[COLOR="Red"] text[/COLOR]"
``` and make it active by the command
```
sudo update-grub
```

I use the following script to start X in Ubuntu 12.04
```
#!/bin/bash

ans="$(ps -A|grep \ lightdm$)"
res=$?
if [ "$res" == "0" ]
then
 echo "x (lightdm) is already running"
else
 echo "x will be started:"
 echo "sudo service lightdm start"
 sudo service lightdm start
fi

```
I store it in the file [FONT="Courier New"]~/bin/x[/FONT] and I have added the following line to the end of .bashrc as a reminder.
```

echo "x to start the graphic desktop environment lightdm"

```

---

### Post by sudodus on 2012-12-23
> **Cookieh said:**
> I believe its possible, as when you boot into an Ubuntu, many different terminals load. They are reached by the function keys (F1,F2, F3...) where F1 is the GUI mode, and others are terminals. I only know this but I dont know how to enter them.

In Ubuntu (and its flavours Lubuntu etc) you enter into the different screens with the following hotkey combinations (press all keys at the same time)

ctrl + alt + F1  (normally a text screen)
ctrl + alt + F2  (normally a text screen)
ctrl + alt + F3  (normally a text screen)
ctrl + alt + F4  (normally a text screen)
ctrl + alt + F5  (normally a text screen)
ctrl + alt + F6  (normally a text screen)

ctrl + alt + F7  (normally the graphic desktop environment)

---

