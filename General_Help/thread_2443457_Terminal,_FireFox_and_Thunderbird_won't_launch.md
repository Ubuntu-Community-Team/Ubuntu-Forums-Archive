---
title: "Terminal, FireFox and Thunderbird won't launch"
date: 2020-05-15
forum: General Help
---

### Post by sdscotti on 2020-05-15
I have a really annoying problem with an 18.04 install on a VPS server.  I used these instructions to add a desktop and a VNC server.

[URL="https://www.cyberciti.biz/faq/install-and-configure-tigervnc-server-on-ubuntu-18-04/"]https://www.cyberciti.biz/faq/install-and-configure-tigervnc-server-on-ubuntu-18-04/

[/URL]That seems to work well, and I can VNC in as root or as a sudo user.  I cannot launch firefox, thunderbird or the terminal, but I can launch most other apps it seems.


Is there a log file somewhere on the system that I can look at to see what the problem is ?

---

### Post by TheFu on 2020-05-15
Don't run gui programs as root or using sudo.  That often breaks all sorts of things. it may have broke the ability for a normal user to run gui programs.  

Using a remote root connection shouldn't be possible with a stock ubuntu install. Normally the root account is disabled.

Security of VNC is pretty bad.  i see the how-to says to use ssh tunnelling. There's a way to start the vncserver to prevent any non-localhost connections.   The use of Gnome3 is a poor suggestion, imho. Gnome3 is really heavy for a remote connection.  Almost any other DE would be better.

Rather than vnc + ssh complexities, perhaps an x2go solution would be better and easier.

Most log files are in /var/log/

---

