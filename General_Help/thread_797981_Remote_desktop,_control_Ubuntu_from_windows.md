---
title: "Remote desktop, control Ubuntu from windows"
date: 2008-05-17
forum: General Help
---

### Post by Trzone on 2008-05-17
I would like to control my ubuntu pc from my windows laptop, anyone know how to do this? thank you.

---

### Post by chrisccoulson on 2008-05-17
If you want to control the desktop, you can use VNC. To enable a VNC server, go to System -> Preferences -> Remote Desktop and check 'Allow other users to view your desktop' and 'Allow other users to control your desktop'.

Then install your preferred VNC client on your Windows laptop

---

### Post by scxtt on 2008-05-17
i believe this only works if you're already logged in (assuming it's still vino) ~ you'd want an actual VNC server running (tightvncserver) to be able to connect at any time ...

---

### Post by daimaru on 2008-05-17
I like [www.nomachine.com](www.nomachine.com) at least if you want graphical control of your desktop. It seemed much faster than the other vnc stuff i tried. This is not necessarily the best option because I have only just started using that tech. 

The thing i did notice was that remote desktop through vnc server or whatever its called was extreemly slow, whilst nomachines nxclient was nice and fast.

you need to install ssh server for it to work cause it uses ssh on port 22 to connect to your remote machine.

---

### Post by Trzone on 2008-05-17
What about if i want to connect to the box at work? How would i do that?

---

### Post by bodhi.zazen on 2008-05-17
Depends on your configuration. Do you use a router ? I like to connect over the interned using ssh.

[uwiki]VNC[/uwiki]

[uwiki]VNCOverSSH[/uwiki]

---

