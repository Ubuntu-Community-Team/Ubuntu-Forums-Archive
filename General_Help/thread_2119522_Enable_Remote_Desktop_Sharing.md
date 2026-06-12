---
title: "Enable Remote Desktop Sharing"
date: 2013-02-24
forum: General Help
---

### Post by manu08 on 2013-02-24
Hi,

I installed Lubuntu 12.10 on an old HP notebook. I was hoping to enable Remote Desktop Sharing so I could put away the machine and continue to access/control it via my iPad. Currently I use an app called CloudConnect Pro for my other Windows or Mac computers. It [states online]("http://antecea.com/apps/cloud_conn_pro/technical.html") that the app supports both VNC and RDP protocols.

Can somebody help me understand how to achieve this please?

I'm very new to Lubuntu so simplified instructions would really help :)

---

### Post by SteveDee on 2013-03-02
I know nothing about CloudConnect, but you need to start by installing a VNC server on your Lubuntu notebook.

There are several servers to choose from, but I suggest you install x11vnc

Once installed, open terminal and type: x11vnc -forever -display :0

Now see if you can access your Lubuntu machine from your remote machine.

If this works, you can then create a script so that vnc server starts when the Lubuntu machine runs:-
 #!/bin/sh
 x11vnc -forever -display :0

...and call the script: startvnc.sh
...and make the file executable.

This script then goes into an autostart directory...but I will explain more if you get the first bit working.

---

