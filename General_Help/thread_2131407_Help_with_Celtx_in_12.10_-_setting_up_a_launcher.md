---
title: "Help with Celtx in 12.10 - setting up a launcher"
date: 2013-04-01
forum: General Help
---

### Post by byrdiblack on 2013-04-01
I'm piggy backing off of this post with a follow up question: [http://ubuntuforums.org/showthread.php?t=1775663&p=12582715#post12582715](http://ubuntuforums.org/showthread.php?t=1775663&p=12582715#post12582715)

I was able to launch Celtx in Ubuntu 12.10 by moving the extracted file to the home folder and launching it from the terminal. 
I was wondering if anyone could provide me with detailed linux newbie instructions on creating a launcher so that I can have Celtx open from the dock every time I need it?

[COLOR=#000000]I'm currently using Ubuntu 12.10 and when I right click the Celtx app icon as it's running and lock it to the dock, it just becomes a floating icon with no click response after the program closes. I'd love to learn about creating a launcher that will work! Thanks in advance![/COLOR]

---

### Post by r0ck1t on 2013-04-28
I followed the installations instructions on the Celtx wiki, and this is exactly what I did to make my launcher.

Press Ctrl + Alt + T to bring up a Terminal window.

```
gedit ~/.local/share/applications/celtx.desktop
```

Copy and paste this text into that file.

```
[Desktop Entry]
Name=Celtx
Comment=Screeplay Editor
Exec=/usr/local/celtx/celtx
Icon=/usr/local/celtx/icons/default48.png
Terminal=True
Type=Application
StartupNotify=True
```

Save and close gedit.

Press the windows\super key and type in celtx, the launcher will be available, just drag and drop it into the the launcher and it will be locked in there.

---

### Post by elisha.ryder on 2014-01-09
Unfortunately, the instructions given here are not working for me.  I can launch Celtx with ./celtx from the terminal after navigating to the location where Celtx is, but neither the above manual launcher creation instructions nor the gnome-desktop-item-edit instructions I've found are creating a launcher that works.  Since I can launch the program from the terminal, it seems to me that I should be able to create a launcher...but no dice.  What gives?

Also total newb, running 13.10

---

