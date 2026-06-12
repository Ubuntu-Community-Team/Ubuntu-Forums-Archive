---
title: "Getting an additional mouse button to work"
date: 2014-11-22
forum: General Help
---

### Post by Ktost on 2014-11-22
Hello. I am a user of Ubuntu 14.04.01 and a mouse Gembird MUSG-001. Now, this mouse has an additional DPI changing button. It's detected and it works properly on Windows but Ubuntu doesn't detect it when clicked (tested with xev). I have found [this]("https://help.ubuntu.com/community/MouseCustomizations") guide but unfortunately, I don't have that needed xorg.conf file and I don't know how to get it. Can you help me, please?

---

### Post by ajgreeny on 2014-11-22
I have not read all the details of your linked web-page, but in normal circumstances, if you make a new /etc/X11/xorg.conf file it will be used by the system.

So write an xorg.conf file in your home, with a text editor (gedit, I presume in Ubuntu 14.04.1) with content as shown in that link, then move it to /etc/X11 with ```
sudo mv xorg.conf /etc/X11/xorg.conf
```Finally, logout and log in again to restart an xsession where you can test the mouse button activity.

---

