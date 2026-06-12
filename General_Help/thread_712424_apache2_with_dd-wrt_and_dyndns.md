---
title: "apache2 with dd-wrt and dyndns"
date: 2008-03-01
forum: General Help
---

### Post by tmetzcc325 on 2008-03-01
Hello all,

I am not sure if this is the proper place for this post, but I can't think of anywhere else.  Right now I am running apache2, pure-ftpd and ssh.  I have set up an account at DynDNS.com, and have setup my Buffalo G125 router (with DD-WRT installed) to forward ports 80, 21, and 22 to my PC (which has a static IP).

The problem has to do with accessing the web server from OUTSIDE the LAN.  From work, I can ssh and ftp to this PC using the domain name I have set up at DynDNS, but I cannot get to any web pages on this PC.  I have apache set up to listen on port 80, set up the document roots and everything, and I can access it from other PCs on the LAN, just not from anywhere else.  It is driving me up a wall.

I am thinking it is a problem with the port forwarding on DD-WRT, but can't for the life of me figure out why it is properly forwarding the FTP and SSH requests, but not HTTP.  I have tried forwarding a whole slew of ports for HTTP, including updating the listen port in apache, but to no avail.

Does anyone have any ideas why this could be happening?  Has anyone else experienced a similar issue?  Please let me know what other information anyone might need to help me with this.

Thanks in advance,
Tom

---

### Post by mnmleon on 2008-06-16
have the same problem, have checked with isp to make sure they're not blocking ports too.

---

### Post by Rhubarb on 2008-06-16
I'm using dd-wrt here, and I can access my apache2 server fine from the net.
Just forwarding port 80 TCP to my server, and it works fine for me.

Probably won't work, but try re-booting your router.

---

### Post by tmetzcc325 on 2008-07-18
Have you had any luck with this mnmleon?  I am still stumped.

---

