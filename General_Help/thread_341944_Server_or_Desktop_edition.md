---
title: "Server or Desktop edition?"
date: 2007-01-19
forum: General Help
---

### Post by c_pradelli on 2007-01-19
Hello,

I need to setup a server in my office. 
The server is an HP Xeon dual core with 2GB ram and 1TB sata disks.

Does the server edition give me better performance than the desktop edition on this server?.
I'm asking this because I prefer to manage the server by a graphical desktop like xfce or gnome.

---

### Post by x64Jimbo on 2007-01-19
Install from the server disc. Then, install the desktop with the following command:
sudo aptitude install xubuntu-desktop
The desktop version comes bundled with a lot more programs than you probably need, and the last thing you want on a network is a server with unneeded packages (and possibly flaws/bugs/exploits). 
If you add users at any point, you may want to watch out for this: when I was fiddling with Ubuntu in a server role, it automatically made all new users sudoers, which as you might imagine is NOT the desired effect.

---

### Post by taurus on 2007-01-19
In that case, install the desktop version and then install whatever server apps you want.  That way, you have Gnome to configure all your stuff.  It works just as good.

---

### Post by c_pradelli on 2007-01-19
So, both Server and Desktop edition have the same performance at kernel level for server applications?, you mean that the only difference are the programs that are bundled in each case?

Thank you very much in advance.

---

### Post by taurus on 2007-01-19
Server version doesn't come with any window manager so you have to do everything from a terminal/console.  However, you can still install a window manager to the server version with apt-get or aptitude (not synaptic since it's a GUI app).  Therefore, go for the desktop version and then install whatever else you need like sshd, ftp server, apache2, etc.

---

