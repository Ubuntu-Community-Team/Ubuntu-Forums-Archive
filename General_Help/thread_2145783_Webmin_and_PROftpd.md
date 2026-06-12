---
title: "Webmin and PROftpd"
date: 2013-05-16
forum: General Help
---

### Post by komrad3006 on 2013-05-16
i installed webmin, and figured out how ot install PROftpd, but does anyone know how or know of a basic guide to help walk me through how to set up a ftp server on it? i made a new user and tried making a new virtual server, just cant seem to get my laptop to connect to it, Im trying to make my dekstop a server so that when i am away from home i can access my school files if need be.

---

### Post by Lars Noodén on 2013-05-16
If it's just you connecting, then I would suggest skipping FTP and using SFTP.  Unlike FTP it is secure, and unlike FTP it is easy to set up.  You get SFTP support out of the box if you install the package openssh-server, no additional configuration is needed.  Though to access your machine from the Internet, you might have to set up port forwarding on your router.  

SFTP clients are built into FileZilla, Nautilus, Thunar and others.  So no special software is needed to connect.

However, it is time to retire FTP

[list]
[*] [http://blog.jdpfu.com/2011/07/10/why-you-need-to-stop-using-ftp](http://blog.jdpfu.com/2011/07/10/why-you-need-to-stop-using-ftp)
[*] [http://www.openlogic.com/wazi/bid/188103/Stop-Using-FTP-How-to-Transfer-Files-Securely](http://www.openlogic.com/wazi/bid/188103/Stop-Using-FTP-How-to-Transfer-Files-Securely)
[/list]

---

### Post by komrad3006 on 2013-05-16
ok i installed openssh-server with terminal, and have it setup and running through webmin but i still cant connect with filezilla client? any suggestion. im reading [http://doxfer.webmin.com/Webmin/SSHServer](http://doxfer.webmin.com/Webmin/SSHServer) to help me out but still not working.
*EDIT: yes my router is forwarded on port 22

---

### Post by Lars Noodén on 2013-05-17
Can you connect locally on the same LAN?

To connect using FileZilla file in the Host, Username, Password and Port at the top of the window.  The port should be 22 for SSH.

---

