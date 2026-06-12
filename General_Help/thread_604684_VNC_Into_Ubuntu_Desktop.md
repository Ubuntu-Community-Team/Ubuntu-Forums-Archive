---
title: "VNC Into Ubuntu Desktop"
date: 2007-11-06
forum: General Help
---

### Post by nami on 2007-11-06
Hi

I have Ubuntu 7.10 at home and Windows XP at work.  ONLY the internet port is open via the proxy server and firewall at work.

So, how do I vnc into my home computer from my work computer?

---

### Post by az on 2007-11-06
> **nami said:**
> Hi

I have Ubuntu 7.10 at home and Windows XP at work.  ONLY the internet port is open via the proxy server and firewall at work.

So, how do I vnc into my home computer from my work computer?

Vino-server is the remote desktop program on Ubuntu that is installed by default.  You can change the port by editing it's configuration settings using the gconf-editor.

run

gconf-editor

at the command line.

Then forward that port to your Ubuntu box with your router.

---

### Post by nami on 2007-11-06
Thanks

I will give that a try.

---

### Post by volksman on 2007-11-06
Or if its available to you you can run your VNC session over an SSH tunnel.  Very slick and secure way to hide everything you are doing on your home machine and most firewall admins leave 22 open.

Check out Putty for a windows ssh client and Google can help you read up on creating tunnels.

---

### Post by az on 2007-11-06
> **volksman said:**
> Or if its available to you you can run your VNC session over an SSH tunnel.  Very slick and secure way to hide everything you are doing on your home machine and most firewall admins leave 22 open.

Check out Putty for a windows ssh client and Google can help you read up on creating tunnels.

You can also run xming on your windows box, ssh into your Ubuntu box at home and run remote applications on your windows desktop.

---

### Post by nami on 2007-11-20
will any of these solutions allow me to access my desktop via a webpage?

---

