---
title: "Specify terminal in launcher"
date: 2013-05-16
forum: General Help
---

### Post by nullgraph on 2013-05-16
Hi, I followed the this [guide]("http://netgator.blogspot.com/2012/08/how-to-add-shortcut-icon-on-panel-in.html") to add my own launcher to panel. I tested my .desktop file, the script opens in gnome-terminal and it works fine. But after added to panel, the script is opened in LXTerminal and does not work. (If you're curious, this is to start [GAP]("http://gap-system.org/")). I don't know why it doesn't work in LXTerminal, as a work around, is there anyway to specify which terminal is used?

Here's my .desktop file

```

[Desktop Entry]
Version=1.0
Type=Application
Terminal=true
Icon[en_US]=gnome-panel-launcher
Name[en_US]=GAP 4.6
Exec=/usr/local/bin/gap4r6/bin/gap.sh
Name=GAP 4.6
Icon=gnome-panel-launcher
Categories=Development;
StartupNotify=true

```

And here's the part I added to the panel file
```

Button {
            id=/usr/share/applications/gap4r6.desktop
            terminal=1
        }

```

---

### Post by humpty88 on 2013-05-29
Maybe..

Exec=gnome-terminal -e /usr/local/bin/gap4r6/bin/gap.sh

---

