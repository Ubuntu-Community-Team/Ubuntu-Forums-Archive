---
title: "Should I use passive mode for proftpd?"
date: 2008-03-07
forum: General Help
---

### Post by Jordanwb on 2008-03-07
I have Ubuntu Server 7.10 installed on my low end server. I installed proftpd by typing: sudo apt-get install proftpd, it asked if it was initd or standalone. I selected standalone and I could use ftp. What I want to know is that in ALFTP and I want to connect should I put the tick mark in passive mode? I read about passive mode online but I still don't understand how it works. I understand protocols and ports and that.

Thanks.

---

### Post by SpaceTeddy on 2008-03-08
in my opinion, ftp is an outdated protocoll. In a world where every thing behind NATs it does not work properly anymore... 

That said, i think this is how FTP works

The FTP port (21) is the controll port. It issues the commands what shall be done, displayed, uploaded, downloaded, etc. It controlls the session, so to say. This is (in standard config) always and only done on port 21...

In active FTP mode, once you have initiated a connection to an ftp server, the server will try to contact you in return on port 20 (ftp data transfer). This connection is going reverse and WILL NOT pass thought any NAT router on the way that you are behind (unless it is specificially configured to do so). i.e. you will be able to connect to the server, but not able to open a data connection to it, since the server cannot find you. It will result in a you not being able to see the result of issued commands on the server.

In passive mode, data connection is not issued by the server, but also by your computer - to the server. This will allow you to use the FTP even if you are behing a NAT router/firewall...

As for if you should use passive or not - depends on the circumstance. But in general, i would suggest that you do use it, since it does not need the backwards connection and is therefore usuable in more scenarios.

Sidenote:
If i might also add a personal opinion on ftp - don't use it. It is entirely outdated and too bulky. Given, it is a fast protocol with low overhead, but that is to the cost of security. All ftp connections (some ftp server support TLS/SSL by now) are entirely unencrypted, meaning anyone can sniff your traffic and/or username/password combinations.

If it is essential that you use ftp - oh well, nothing to be done. 
Otherwise, i would suggest the sftp that comes with openssh or webdav in apache which can be configured to run over SSL

---

### Post by Jordanwb on 2008-03-08
I've set up port forwarding for port 21 on my router but not for 20 but I haven't had any problems with using active FTP (go figure). I'm not entirely concerned about security because I'm using it as a development server.

Thanks.

---

