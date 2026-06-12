---
title: "How can I connect to my Linux desktop ?"
date: 2007-11-06
forum: General Help
---

### Post by N3tpr0be on 2007-11-06
Hello  all. I have a computer at home running Ubuntu 7.10. Now.. how can I connect to my computer like remote desktop windows has and login on the root user, and actually feal like I`m at my computer at home .. ?

Thanks in advance

---

### Post by scrooge_74 on 2007-11-06
Like I dont understand the questions completetly. Do you have another Linux computer you neeed to connect? Is a Windows computer you are going to use? 

Do you need to use the GUI? Like you need to give more details in order for someone to help you

---

### Post by Craigus on 2007-11-06
[http://www.ubuntugeek.com/share-your-ubuntu-desktop-using-remote-desktop.html]("http://www.ubuntugeek.com/share-your-ubuntu-desktop-using-remote-desktop.html")

---

### Post by zaphod777 on 2007-11-06
> **Craigus said:**
> [http://www.ubuntugeek.com/share-your-ubuntu-desktop-using-remote-desktop.html]("http://www.ubuntugeek.com/share-your-ubuntu-desktop-using-remote-desktop.html")

your link doesn't work. Yes you can use VNC. it is like RDP but for linux all port forwarding and firewall rules aply.

---

### Post by scrooge_74 on 2007-11-06
easier way if the OP wants to use the GUI in another Linbox

CTRL+ALT+F2
log in
xinit /usr/bin/xterm -- :1
then ssh -Y username@anotherbox

gnome-session for Ubuntu
startkde for Kubuntu
startkfce4 for Xubuntu

---

### Post by volksman on 2007-11-06
VNC is not fun across a WAN.  Try Nomachine NX as it does the same thing as RDP.  Only two issues with it are you can't connect to the "console" so if you have a desktop already open and want to attach to it it can't be done (however I think there MAY be a way with v3).  Other issue is that if you use Compiz it may mess with NX's ability to properly display the desktop.  I've found that disabling the rendering component in NX gets the connection working but it doesn't look pretty.

---

