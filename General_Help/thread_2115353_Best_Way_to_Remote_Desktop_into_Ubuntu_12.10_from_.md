---
title: "Best Way to Remote Desktop into Ubuntu 12.10 from Windows 7 (LAN)???"
date: 2013-02-12
forum: General Help
---

### Post by kromix on 2013-02-12
Problem:


LAN Network at work.

Want to remote INTO Ubuntu 12.10 from Windows 7 locally.

I enabled Desktop Sharing in Ubuntu and downloded VNCViewer and Remoted that way, but it's really slow.

When I RDP from my Windows Box to another Windows box, even a server at the Data Center its nice and quick...

What is the best solution?

I'm remoting from a Windows 7 Desktop to an Ubuntu Laptop, but it's dreadfully slow.

Thanks!

---

### Post by cjhabs on 2013-02-12
I use NX from NoMachine.com - you load the NX server on the Ubuntu machine and the NX client on the Windows box (or Mac or Linux) - open up port 22 - load the extra fonts if neccessary - depends on the apps you are using. It works great and is really fast.
The free version supports 2 named users logging in simultaneously.

---

### Post by kromix on 2013-02-12
> **cjhabs said:**
> I use NX from NoMachine.com - you load the NX server on the Ubuntu machine and the NX client on the Windows box (or Mac or Linux) - open up port 22 - load the extra fonts if neccessary - depends on the apps you are using. It works great and is really fast.
The free version supports 2 named users logging in simultaneously.

Is this good for LAN though??

---

### Post by |{urse on 2013-02-12
I like xrdp for that, super easy to install and use.

[http://www.liberiangeek.net/2012/05/connect-to-ubuntu-12-04-precise-pangolin-via-windows-remote-desktop/](http://www.liberiangeek.net/2012/05/connect-to-ubuntu-12-04-precise-pangolin-via-windows-remote-desktop/)

---

