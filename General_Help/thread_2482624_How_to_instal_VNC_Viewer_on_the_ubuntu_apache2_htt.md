---
title: "How to instal VNC Viewer on the ubuntu apache2 http/php/... server ?"
date: 2023-01-06
forum: General Help
---

### Post by frenchn00b on 2023-01-06
Hello,

I run an ubuntu  server for Web. 

I would like to create a site with a VNC Viewer. Have you heard of some way to have a VNC Client on apache2. Likely, it won't be into the repository, I may guess.

Kind regards

example:
[https://github.com/novnc/noVNC](https://github.com/novnc/noVNC)

---

### Post by ActionParsnip on 2023-01-06
Do you mean like a VNC client in a web browser? Is this the requirement?

---

### Post by dragonfly41 on 2023-01-06
Remmina Remote Desktop ??

---

### Post by TheFu on 2023-01-06
> **frenchn00b said:**
> Hello,

I run an ubuntu  server for Web. 

I would like to create a site with a VNC Viewer. Have you heard of some way to have a VNC Client on apache2. Likely, it won't be into the repository, I may guess.

Kind regards

example:
[https://github.com/novnc/noVNC](https://github.com/novnc/noVNC)

"Guacamole" is the project you want.  [https://guacamole.apache.org/](https://guacamole.apache.org/) 
Please don't deploy it. It is quite hackable and making a common web browser the access point for total control of a system is a terrible idea.  There are better options.

a) If you need to run a GUI program on the remote server, using 'ssh -X {username}@{ip}  program options' will display the program on your local system in 1-2 seconds.  Again, all the traffic is encrypted via ssh and the connection is authenticated via ssh.

b) x2go is an NX-based remote desktop solution. It uses ssh for authentication and all network traffic is encrypted using ssh.

c) Cockpit is a remote server management webapp. [https://cockpit-project.org/running](https://cockpit-project.org/running)  I think this is less evil than Guacamole, but still not something I'd deploy.

But I know you won't listen and use straight ssh.  That's was most server admins do.

If you do deploy any web-based tool for this, please, please, please, only allow 'localhost' connections and force an ssh-tunnel be setup. This provides the security that is sorely lacking in all web-based tools.  You can even use an ssh-socks5-proxy script to make this almost automatic.

---

### Post by MAFoElffen on 2023-01-06
> **frenchn00b said:**
> Hello,

I run an ubuntu  server for Web. 

I would like to create a site with a VNC Viewer. Have you heard of some way to have a VNC Client on apache2. Likely, it won't be into the repository, I may guess.

Kind regards

example:
[https://github.com/novnc/noVNC](https://github.com/novnc/noVNC)
To a kiosk type of VM? Or a VM setup to train a specific purpose? or for what? I'm trying to visualize the goal...

---

