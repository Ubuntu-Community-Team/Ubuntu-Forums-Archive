---
title: "Tunneled XVNC connection to Ubuntu 13.04 from Windows 7 client -- painfully slow!"
date: 2013-08-01
forum: General Help
---

### Post by Cambysese on 2013-08-01
Greetings all,
I recently upgraded to UBUNTU 13.04. Prior to the upgrade I was effectively using xrdp to access my unity 2d (gnome-fallback-session) desktop from my windows 7 client. With the upgrade my understanding is that the gnome-fallback-session is no longer available under 13.04, and further the xrdp server could not handle the unity desktop over a remote session. 
As an alternative I am using a tunneled xvnc connection to establish a remote desktop connection between my windows 7 machine and ubuntu 13.04 workstation. Briefly, (i) connect via ssh to the server (ii) startup xvnc server via ```
sudo x11vnc -display :1 -auth guess -q
``` and (iii) use realVNC vncviewer application to access the remote desktop. With this approach I can manage some work, but the connection is awfully slow with bad geometry. Firstly, the refresh rate severely hinders delivery of the remote desktop to the client viewer, although I've already disabled some of the effects & animations in unity. Second, I have very limited control over the geometry of the desktop, thus even scaled down to fit the geometry of the client display the result is a very condensed and disproportional remote desktop view.
I would appreciate any suggestions to either (a) improving the xvnc experience or (b) alternative (but straightforward) solutions for remote desktop access.

Thanks in advance
Kam

---

### Post by lukeiamyourfather on 2013-08-01
There are a lot of options for x11vnc and some of them completely change the experience. This is a command I've used before on a LAN with good results. Check out the manual for all the explanations if needed.

```
x11vnc -noxdamage -nowf -nowcr -noscr -nonap -nowait_bog -wait 5 -defer 1
```

---

