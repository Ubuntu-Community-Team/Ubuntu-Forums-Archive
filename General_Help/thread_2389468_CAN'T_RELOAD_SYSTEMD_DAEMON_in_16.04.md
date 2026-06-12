---
title: "CAN'T RELOAD SYSTEMD DAEMON in 16.04"
date: 2018-04-17
forum: General Help
---

### Post by bradleyestep on 2018-04-17
Hey,
I'm trying to install Tomcat and step 5 is to create a systemD service file, I did that , and now when i make the command:

$  [COLOR=#3A3A3A][FONT=monospace]sudo systemctl daemon-reload

It outputs this error message:

[/FONT][/COLOR]Failed to connect to bus: No such file or directory

How do I get this daemone to reload?  Thanks in advance

---

### Post by dino99 on 2018-04-17
in case you have missed that howto
[https://www.digitalocean.com/community/tutorials/how-to-install-apache-tomcat-8-on-ubuntu-16-04](https://www.digitalocean.com/community/tutorials/how-to-install-apache-tomcat-8-on-ubuntu-16-04)

---

### Post by bradleyestep on 2018-04-17
I'm using that tutorial, but in step 5 this step fails to create the bus connections:

[COLOR=#3A3A3A][FONT=monospace]sudo systemctl daemon-reload
[/FONT][/COLOR][COLOR=#000000]Failed to connect to bus: No such file or directory

its like systemd is not activated or something[/COLOR]

---

