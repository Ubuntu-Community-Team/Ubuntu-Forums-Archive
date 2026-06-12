---
title: "How Do I Install Real VNC Viewer"
date: 2017-01-01
forum: General Help
---

### Post by johnthemong on 2017-01-01
I've recently started using Lubuntu and also recently got myself a Raspberry Pi. The Raspberry Pi uses RealVNC and, while the viewer is easy enough to use on Windows, I can't figure out how to get it on my Lubuntu OS.  I really am reasonably new to all this so feel free to treat me like a complete muppet. 

The website where you get the software is [https://www.realvnc.com/download/viewer/](https://www.realvnc.com/download/viewer/)

Is there any other viewer I could be using instead perhaps?

Thanks in advance.

John

---

### Post by cariboo on 2017-01-01
Remmina is installed by default on Ubuntu, I'm not sure if it is the same for Lubuntu, but it can easily be installed  via the your favourite way of installing software.

---

### Post by gordintoronto on 2017-01-02
My favorite remote desktop client is KRDC. If it's your first KDE application, it will install a whole bunch of other stuff. In my case, k3b is one of the first things I add to a new installation, and it grabs the "whole bunch of other stuff."

---

### Post by alexandari on 2017-01-03
I suggest the following application and method. Remmina is great, it's easier to install and use.

```
apt-get install remmina remmina-plugin-vnc
```

You can use that to connect to any VNC. There are also other protocols that can be used, such as RDP

Cheers

---

