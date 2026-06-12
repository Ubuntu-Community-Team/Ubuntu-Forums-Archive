---
title: "Firewall question, simple."
date: 2008-05-17
forum: General Help
---

### Post by Tanatz on 2008-05-17
Do I need one?  If so, which do I use and how do I install it? edit: using 7.10, not 8.04.

(very new to Kubuntu).

Thanks in advance.

---

### Post by bodhi.zazen on 2008-05-17
As you are new start here :

[Ubuntu Security - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=510812") 

Firewalls can be controversial topics around here and try not to let anyone trolling on the topic bother you too much.

The firewall is iptables and is configured by gui tools or the command line.

If you like, you can look at ufw or guard dog. IMO ufw is superior, but you may not want to use the command line.

Otherwise :

1. Take a look at the link.

2. It is better to ask what is it you want a firewall to do for you ?

---

### Post by Tanatz on 2008-05-17
In Windows in run software like:
Firefox
AIM
utorrent
weatherbug

etc.  I basically want to be able to do this sort of stuff with peace of mind.  Is any further editing of iptables even necessary for this basic type stuff?

---

### Post by bodhi.zazen on 2008-05-17
IMO, not at all.

You need a firewall if you are running a private server or need to restrict access to a public server.

Some people advise you run a firewall for security reasons, depends on how paranoid you are. Probably not necessary if you are not running a server.

---

