---
title: "EDGY- VNC server w/resumable sessions"
date: 2007-02-06
forum: General Help
---

### Post by tiger.woods on 2007-02-06
I want to set up VNC Server on my EDGEY box with resumable sessions. Is there a "How to" around somewhere for that?

If not can someone guide me through it?

TIA.

TW,

---

### Post by grumpymole on 2007-02-07
TW,

There is a long thread [here]("http://www.ubuntuforums.org/showthread.php?t=122402") about resumeable sessions.  Also, check [here]("http://grumpymole.blogspot.com/2006/12/xubuntu-remote-desktop-with-vnc4server.html").

But note that vnc4server, with the _latest_ updates, doesn't work in Edgy and Feisty.  More about that [here]("http://grumpymole.blogspot.com/2007/02/edgy-and-feisty-vnc4server-still-not.html").

Regards

Warren
htp://grumpymole.blogspot.com

---

### Post by tiger.woods on 2007-02-12
Thanks, I got it going but it's not logging into session :0 only creating a new session :1 did I do something wrong?

---

### Post by tiger.woods on 2007-02-12
I uninstalled vnc4sever and installed x11vnc and it was a breeze to setup...

#sudo apt-get install x11vnc
#sudo kate /etc/kde3/kdm/Xsetup (added /usr/bin/x11vnc -forever -rfbport 5900 -bg -o /var/log/x11vnc.log -rfbauth /home/myuser/.vnc/passwd)
$vncpasswd

Then remoted in from 192.168.1.100:0, piece of cake....

thanks for your help.

---

### Post by tworkemon on 2007-02-22
My x11vnc stopped working recently I am assuming its due to the recent dist-upgrades with feisty. Anyone else experiencing this ??

---

### Post by tworkemon on 2007-02-22
Problem was solved by adding -noxdamage to my x11vnc startup line. Never needed this before but I guess its due to the xorg 7.2 upgrades feisty is going through.

---

