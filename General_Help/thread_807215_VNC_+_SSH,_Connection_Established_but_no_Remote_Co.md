---
title: "VNC + SSH, Connection Established but no Remote Control???"
date: 2008-05-25
forum: General Help
---

### Post by RottenBananas on 2008-05-25
Hey guys,
  Been messin around with vnc and ssh. Im goin from an ubuntu laptop to an ubuntu desktop.

I followed this guide:
[https://help.ubuntu.com/community/VNCOverSSH](https://help.ubuntu.com/community/VNCOverSSH)

I can connect using the -via param in vncviewer. So all is good. I see my desktops screen and can access/run everything remotely.

The problem is that I cant control the desktop. If I open up firefox remotely itll show up on my laptops screen but the desktop stays the same. If a user is on my desktop I cant see what they're doing. I've connected but I don't have control

I tried enabling it through preferences/remote desktop and the login window but still no control

Any ideas?

---

### Post by RottenBananas on 2008-05-26
Bump

---

### Post by Gunman1982 on 2008-05-26
Did you do this 'Allow users to see/control my desktop' thing described here: [http://www.debianadmin.com/remote-desktop-sharing-in-ubuntu.html]("http://www.debianadmin.com/remote-desktop-sharing-in-ubuntu.html")

---

### Post by RottenBananas on 2008-05-26
Hey,

Yes I have the 'Allow other users to control your desktop' option checked in my preferences >> remote desktop.

I did everything step by step from this guide
[https://help.ubuntu.com/community/VNCOverSSH](https://help.ubuntu.com/community/VNCOverSSH)

my command to connect looks something like this

on the desktop
```
vncserver :1
```

on the laptop:
```
sudo vncviewer -via myuser@my.ip :1
```

Still no control, I can only view

---

### Post by RottenBananas on 2008-05-26
Forwarding my entire desktop through ssh also works

I use what is shown under the Forwarding X section in this howto

[https://help.ubuntu.com/community/SSHHowto](https://help.ubuntu.com/community/SSHHowto)

So I can view my desktop using vnc+ssh or just using ssh, but i still cant control it.

Any suggestions?

---

### Post by RottenBananas on 2008-05-27
anyone???

---

