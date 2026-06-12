---
title: "How do I start Ubuntu's remote desktop (VNC) via SSH?"
date: 2008-01-02
forum: General Help
---

### Post by m i k e on 2008-01-02
I am going to be using wake-on-lan to boot my computer remotely.  Then I want to be able to connect via VNC.  However, Ubuntu doesn't start the its remote desktop (VNC) service until after you login (which I won't be able to do if I'm not in front of the computer).  **My question is how can I start Ubuntu's remote desktop service via SSH?**  This would work because SSH connections can be made before one logs in.  Thanks for any help.

---

### Post by cdenley on 2008-01-02
```

sudo apt-get install vnc4server
vncserver

```

---

### Post by daengbo on 2008-01-02
Quick question. If you aren't logged in at that computer, what will the VNC server see? I'm not big into VNC, so this may work, but I don't suspect it will.

An easier way to accomplish this (as long as you are on the same network i.e. not across the Internet) is to enable remote login, then log in from the other computer. To do that, go to System -> Administration -> Login window and move to the "Remote" tab. Change "Remote login disabled" to "Same as local," then close the dialog and log out. 

From the other computer, you should be able to choose "Remote login via XDMCP" and access a login screen from the first computer. Log in and all the program will be running on the remote station.

---

### Post by m i k e on 2008-01-02
> **cdenley said:**
> ```

sudo apt-get install vnc4server
vncserver

```

I start the server via SSH and everything looks like its working.  Then however, when I try to connect it acts as if there is no VNC server running.  Any idea why?

---

### Post by cdenley on 2008-01-02
Sorry, it's been a while since I used vnc server. A few more details. The regular ubuntu "Remote Desktop" option is only available since it just makes the existing gnome session already available. vncserver will create a new display for the user vncserver is run as. You can have multiple instances running simultaneously. The port vncserver uses is 5900+display number. So, the first instance of vncviewer would run on port 5901. Another complication is that by default, it doesn't start gnome or kde. Here are instructions for fixing that: [http://faq.gotomyvnc.com/fom-serve/cache/56.html](http://faq.gotomyvnc.com/fom-serve/cache/56.html). Also, apparently, you cannot have two gnome sessions running as the same user. If you are already logged in on the server locally, the vncserver instance you create will fail to start a gnome-session, since one is already running.

An alternative would be to use x11vnc. How this works is it allows you to use a currently running X session remotely. The disadvantages to this are you must use the same resolution as the display on the local machine, and since you're sharing the same session, a local and remote user can't work simultaneously, and you can see each other's activities. Also, it is a little tricky to connect to the gdm login screen.

To use use x11vnc after installing it (sudo apt-get install x11vnc) while not logged in locally:
```

sudo x11vnc -auth /var/lib/gdm/:0.Xauth -display :0

```
as soons as you log in through gdm, vncviewer will get kicked off, but you will be logged in locally

while logged in locally, and connected to ssh as the same user:
```

x11vnc -display :0

```

I think this is the only way to do what you want to do without compromising the security of your system. Also, I assume you are tunneling vnc through your ssh connection, or you are connecting across a trusted network. vnc is not considered a secure protocol.

---

