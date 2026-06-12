---
title: "Lost resolution completely"
date: 2020-07-23
forum: General Help
---

### Post by doc1623 on 2020-07-23
I have a 42 inch LG and it was working but it doesn't now. Now the resolution is so low that I can't use the gui. I've tried to stop and startx. I tried to switch between wayland and xorg. I can't even ssh -Y from another box

/usr/bin/xauth:  timeout in locking authority file /home/larry/.Xauthority


I enter the password but it beeps and shows me the same screen. I can go to another console and log in on the command line.

---

### Post by doc1623 on 2020-07-23
Now getting a slightly different message on the ssh -Y

/usr/bin/xauth:  /home/larry/.Xauthority not writable, changes will be ignored

Where does ubuntu store resolutions/monitors data?

Wayland doesn't work it ask for the password again. I can get to Xorg but again the resolution is unusable. When I look at the resolution box it's empty.

---

