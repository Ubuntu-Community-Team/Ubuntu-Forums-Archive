---
title: "Vncserver"
date: 2006-07-05
forum: General Help
---

### Post by gabbar_singh on 2006-07-05
Hello,
I want to connect to my desktop(Ubuntu) from my laptop(windows xp home) using vnc. I started the vnc service on the desktop. But when I connect to my server, the client gives the error
"Unable to connect to host. Connection refused(10061)"
any help would be apprieciated.
-sakya

---

### Post by ape on 2006-07-05
What display are you attempting to connect to from your Windows machine?  By default, if you already have X running, vncserver will start up on display :1, so from your Windows machine you would have to enter <hostname>:1 in the host dialog.

---

### Post by DirtDart on 2006-07-05
What IP addresses (host and client) are you using?  and are you connecting to the right port?

For example, if you want to connect to your machine, with the machine running vncserver having an IP address of 192.168.0.1, you would want to run:

**vncviewer 192.168.0.1:1**

The number after the colon might be different, depending on your configuration.  A **ps -ef | grep vnc** should give you want port (:1 for example) to connect to.

---

### Post by gabbar_singh on 2006-07-05
I use <ipaddress>:1 to access it
when i  ps -ef | grep vnc
i get
gabbar   10765  8918  0 14:39 pts/0    00:00:00 grep vnc

---

### Post by max_headroom on 2006-07-05
How did you configure your VNC server to start on your ubuntu machine? 

I believe that the standard install adds vino to the system.  The configuration for this can be accessed either by System -> Preferences -> Remote Desktop or by running vino-preferences from the terminal

You can set the options to "Allow other users to view your desktop" and to "Allow other users to control your desktop" and it shows the command needed to access your desktop.

If that is the package that your are using, go ahead and give that a shot and see if it works. If not, could you provide details on the vnc server that your are using?

---

### Post by gabbar_singh on 2006-07-05
surprise solution.. 

I can connect when I do <hostname>:0
but i dont know how...
-s

---

### Post by scxtt on 2006-07-05
vino "shares" your :0 connection, whereas programs like *vncserver create a new "session" on :1, :2, :3, etc. ...

---

