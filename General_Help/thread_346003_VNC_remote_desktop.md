---
title: "VNC remote desktop"
date: 2007-01-25
forum: General Help
---

### Post by lmyint on 2007-01-25
I have a Ubuntu 6.10 desktop and I need to be able to connect to it via VNCviewer, how do I do it? My workstation is an xp box and has tightVNC installed on it.

---

### Post by DoKFr on 2007-01-25
hi

try xvncviewer

---

### Post by Nik_Doof on 2007-01-25
First you need to enable the VNC server, in your settings theres a Remote Desktop option. Tick on enable and set a password. Then you just need to open TightVNC on your XP machine, put in the IP of the Ubuntu PC and connect, it should ask you for your password and connect up.

I've had better experiences with UltraVNC on Windows, not sure why it just seems to work better, but ig uess its down to personal preference.

---

### Post by tombott on 2007-01-25
VNC is built into Ubuntu 6.10.

If you wish to connect to your Ubuntu box from your XP box then you will need to enable VNC on your Ubuntu box.

From the terminal:
```

gconf-editor
```

This will open the Configuration Editor.

Expand desktop - gnome - remote_access

[IMG]http://www.tombott.co.uk/ubuntu/remote.png[/IMG]

In the Top right hand window put a tick in Enabled
I like to have the prompt_enabled ticked, but this is not necessary
Then set a password in the vnc_password section.

You may need to restart your machine for this to take effect but I am not 100% sure.

If you want to connect to your XP box from Ubuntu then use Terminal Server Client Applet

Internet - Terminal Server Client

Change the Protocol to VNC and enter the IP address of your XP box.

Hope that helps.

Tom.

---

### Post by lmyint on 2007-01-25
Do you know where the 'vncserver' file is located? In RHEL4 it's under /etc/init.d

---

### Post by lmyint on 2007-01-25
I did the remote desktop part but it's still not working. When I try to connect to the machine, I get an 'failed to connect to server' error.  What's the name of the file that starts the service?

---

