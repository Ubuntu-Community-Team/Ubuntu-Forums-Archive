---
title: "best way of remote desktop connection from Windows to Ubuntu"
date: 2008-03-09
forum: General Help
---

### Post by qns8dn3 on 2008-03-09
What do you think is the best way of achieving remote desktop connection from a Windows desktop to a Ubuntu desktop? (which protocol, which windows client app, which ubuntu server app and what appropriate setting.)

I want it to be as responsive as Remote Desktop Connection between windows desktops and i want it to be secure.

---

### Post by xc3RnbFO8P on 2008-03-09
Here is a howtos:

[http://howtoforge.com/configure-remote-access-to-your-ubuntu-desktop]("http://howtoforge.com/configure-remote-access-to-your-ubuntu-desktop")
[http://www.debianadmin.com/remote-desktop-sharing-in-ubuntu.html]("http://www.debianadmin.com/remote-desktop-sharing-in-ubuntu.html")
[http://onlyubuntu.blogspot.com/2007/03/sharing-ubuntu-desktop-using-remote.html]("http://onlyubuntu.blogspot.com/2007/03/sharing-ubuntu-desktop-using-remote.html")

---

### Post by qns8dn3 on 2008-03-09
the three howtos suggest to use the free edition of vnc viewer from realvnc. The viewer doesn't support encryption of whole remote desktop session. And it is not as fast as Windows RDP.

---

### Post by harold4 on 2008-03-09
Tunnel through SSH

---

### Post by xc3RnbFO8P on 2008-03-09
> **harold4 said:**
> Tunnel through SSH

[http://www.techotopia.com/index.php/Remote_Access_to_the_Ubuntu_Linux_Desktop]("http://www.techotopia.com/index.php/Remote_Access_to_the_Ubuntu_Linux_Desktop")

---

### Post by scottro on 2008-03-09
Free NX is pretty good, I find it much quicker than VNC.  I haven't configured it on Ubuntu, just Fedora and CentOS.  The Fedora version has a few oddities, which made it a bit of a pain.

If you only need to have on machine access the Windows desktop,   [http://nomachine.com/](http://nomachine.com/) has a free version of their server, which is easier to set up--or perhaps it simply has better documentation.  You can install it on the Ubuntu machine and use their client, also free, on Windows.

---

### Post by HermanAB on 2008-03-09
The best way? 
Xming and PuTTY.

---

### Post by KeyserSoze93 on 2008-03-09
> **HermanAB said:**
> The best way? 
Xming and PuTTY.

Yes, it works a treat for me...

You can also use WinSCP to transfer files off you ubuntu box.

---

