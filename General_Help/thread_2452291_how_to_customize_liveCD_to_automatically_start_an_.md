---
title: "how to customize liveCD to automatically start an app?"
date: 2020-10-20
forum: General Help
---

### Post by jsun-7 on 2020-10-20
I managed to build my own ubuntu liveCD which can boot up a PC successfully.

What is the way to start an app automatically?  I know I have to create an file under /home/ubuntu/.config/autostart/.  But where is that place when I build the liveCD?  In my root system, I can't even find /home/ubuntu directory.  It must be copied over at runtime from somewhere else.  Any pointers?

Thanks.

---

### Post by jsun-7 on 2020-10-25
Just want to answer my own question.  It turns out be pretty easy.   Just create a desktop file and put under /etc/skel/.config/autostart.  Then the livemedia user (aka ubuntu) automatically has it started.

The detailed content of desktop file seems related to desktop manager.  Easiest thing is to create such a launcher on the desktop on your PC.  And then copy the desktop file over.

As an example, here is my file, Electrum.desktop.  It automatically starts electrum bitcoin wallet ([https://github.com/monkey-jsun/eroas](https://github.com/monkey-jsun/eroas))

```

[Desktop Entry]
Version=1.0
Type=Application
Name=Electrum Wallet
Comment=The best open source bitcoin wallet
Exec=/usr/local/bin/electrum -p 127.0.0.1:9050
Icon=/home/ubuntu/.local/share/electrum-logo-128px.png
Path=/home/ubuntu
Terminal=false
StartupNotify=true

```

---

