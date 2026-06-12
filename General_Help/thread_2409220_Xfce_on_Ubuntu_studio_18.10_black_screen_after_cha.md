---
title: "Xfce on Ubuntu studio 18.10 black screen after changing resolution"
date: 2018-12-29
forum: General Help
---

### Post by eufex1 on 2018-12-29
Hi
Does anyone know which config file I need to amend to get the system working again? The usual ones/locations aren't there. 
I would suggest that as its 2019 almost that changing screen resolution from the supplied GUI tools should not kill a system. Hey ho.

Thx in advance for any help forthcoming.
Cheers

---

### Post by again? on 2018-12-29
At the greeter log into a tty (ctrl+alt+F1)
Login and then run...
```
xfconf-query --reset --recursive -c displays -p /
```
which effectively removes the file **~/.config/xfce4/xfconf/xfce-perchannel-xml/displays.xml**

Testing here, deleting that file achieves the same result.
**~/.config/xfce4/xfconf/xfce-perchannel-xml/displays.xml** will be recreated with default values next time you open
Settings > Display

FYI you can monitor the changes or creation of this file by running.
```
xfconf-query -m -c displays
```
then opening Settings > Display

eg monitoring after I deleted ~/.config/xfce4/xfconf/xfce-perchannel-xml/displays.xml
then opening xfce4-display-settings from another terminal.
[ATTACH=CONFIG]282036[/ATTACH]

See ...
```
man xfconf-query
```

---

### Post by eufex1 on 2018-12-30
Thanks, I'll check it out now and get back. I've got a test build on a laptop with the same OS (although 18.04) and displays.xml doesn't exist though -I found that out last night. Does changing resolution via the gui create a displays.xml?

---

### Post by eufex1 on 2018-12-30
Super :) that's got me back to a desktop. So it creates that file if you change, otherwise it runs default.

Can't thank you enough ...
Thank you

---

### Post by again? on 2018-12-30
Yes ...you could rename/move the **~/.config/xfce4** folder to reset most of your user settings.
```
mv ~/.config/xfce4  ~/.config/xfce4.bak
```

Default values mostly come from /etc/xdg

---

