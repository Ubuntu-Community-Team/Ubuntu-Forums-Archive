---
title: "Remote Desktop for Windows"
date: 2007-09-24
forum: General Help
---

### Post by ev5unleash1 on 2007-09-24
Is it passable or is there free software out there that will let me remotely connect to another computer with Ubuntu FROM a Windows PC. I wanna be able to manage my Ubuntu desktop though my laptop and it's running Windows, I know I have Ubuntu on it but I don't always use it.

---

### Post by janarene on 2007-09-24
You want to look at TightVNC for windows at [http://www.tightvnc.com/](http://www.tightvnc.com/).  Just install the  Viewer if you just want to control from the windows box, or install the Server as well if you ever want the Ubuntu box to control the Windows one.  The ubuntu computer should already have Krfb (kubuntu) or Remote Desktop (ubuntu) installed.  Configure  either of them to accept a connection with a password and turn OFF the confirmation request.

---

### Post by dad311 on 2007-09-24
Try NXClient/NXServer.  Easy to install, all the deb and exe files are located at the link pasted below.  I believe there is also a demo at the link below.

[http://www.nomachine.com/](http://www.nomachine.com/)

---

### Post by trippinnik on 2007-09-25
I always liked how I could do so much from the command line using SSH, it's also more secure than VNC at least, and faster over the network.

---

### Post by bodhi.zazen on 2007-09-25
> **trippinnik said:**
> I always liked how I could do so much from the command line using SSH, it's also more secure than VNC at least, and faster over the network.

Tunnel vnc over ssh :

[uwiki]VNC[/uwiki]
[uwiki]VNCOverSSH[/uwiki]

ev5unleash1: See those two links, although FreeNx will also work.

[uwiki]FreeNX[/uwiki]

---

### Post by ev5unleash1 on 2007-10-04
Thanks everyone, You gave me a reason to take Ubuntu off one of my PCs. Arent you happy?:):):):):)

---

### Post by bodhi.zazen on 2007-10-04
Ubuntu off :(

Windows off :)

---

