---
title: "Need answers on configuration file for server."
date: 2005-11-01
forum: General Help
---

### Post by irv on 2005-11-01
:confused: What configuration file do I set port access on a Ubuntu server? After installing webmin on my server, I get an access denied to my desktop which is running Ubuntu. Also I am not sure if a firewall got installed when I installed Ubuntu server 5.10. My serer is on a separate PC (a 500Mhz machine). I set the server up without GUI, and I am not sure what conf. File I need to set access’ in. I have had other thread out here but have not got the right answers yet? Can someone help out a lost soul find his way?

The access denied is from my web browser using ([https://(server](https://(server) ip-address):10000.

---

### Post by l33tc0d34 on 2005-11-01
i have problem too with black screen and no access. i think from google it is safe to fix this problem by

sudo gedit /etc/inittab

and look for line id:2:initdefault: and change to id:6:initdefault: then rebooting pc.

---

### Post by felix_stegerman on 2005-11-01
[QUOTE=irv]:confused: What configuration file do I set [webmin] port access on a Ubuntu server?[/QUOTE]

From the webmin faq ([http://www.webmin.com/faq.html):](http://www.webmin.com/faq.html):)> 
How can I change Webmin's list of allowed IP addresses from the shell?

The file you need to modify is /etc/webmin/miniserv.conf , in particular the allow= or deny= lines. If the allow= line exists, it contains a list of all addresses and networks that are allowed to connect to Webmin. Similarly, the deny= line contains addresses that are not allowed to connect. After modifying this file, you need to run /etc/webmin/stop ; /etc/webmin/start for the changes to take effect. Naturally, the file can only be edited by the root user.

Edit: just remember to keep your LAN safe w/ a firewall ;-)


Felix

---

### Post by felix_stegerman on 2005-11-02
Alternatively, if you have ssh installed on the server, you could (on the client)
run:
# ssh -L 8090:localhost:10000 <server-name-or-ip>
After which you should be able to access webmin on the client as
[http://localhost:8090](http://localhost:8090)

This is a bit safer than allowing everyone (maybe just you LAN) access to
webmin.


Felix

---

