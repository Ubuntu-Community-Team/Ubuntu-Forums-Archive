---
title: "Dynamic DNS"
date: 2013-05-11
forum: General Help
---

### Post by OR83 on 2013-05-11
Does anyone know if the ddclient for DynDNS.com work with No-IP.com? I'm not able to download the noip2 D.U.C I get an:
[COLOR=#ff0000][I]or@or-Satellite-L305:~$ sudo apt-get install noip2
[sudo] password for or: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package noip2[/I][/COLOR]

I was only able to download the ddclient for DynDNS

---

### Post by prodigy_ on 2013-05-11
ddclient [doesn't fully support no-ip.com](http://sourceforge.net/apps/trac/ddclient/ticket/67) yet. Try [noip2](https://help.ubuntu.com/community/DynamicDNS#no-ip) package instead.

---

### Post by OR83 on 2013-05-11
I have but I can't get the no-ip DUC to download

---

