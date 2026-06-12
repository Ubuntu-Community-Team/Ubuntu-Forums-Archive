---
title: "SSH &amp; Authorized keys"
date: 2008-04-26
forum: General Help
---

### Post by Naatan on 2008-04-26
Hi,

I have 2 servers running.. one web server for general usage and one nagios server which I'm still trying to configure, to keep things simple I'm gonna refer to the web server as the server and to the nagios server as the client.

On the client the nagios user was automatically created upon installing nagios, on the server I manually created the user. 
Now on the client I generated an ssh key using "ssh-keygen -t dsa -f ~/.ssh/id_dsa"

I then copied the id_dsa.pub contents over to the authorized_keys2 file on the server.

In both cases I did this for the ~/.ssh/ path under the nagios user.

Now when I try to connect the client to the server using "ssh nagios@server" I get prompted for a password.

I've been trying for one hour now but I can not figure this one out.. anyone know why this might be happening?

---

### Post by Monicker on 2008-04-26
During the key generation you should have been prompted to chooose a password or leave it empty.  Which did you select?

Also, is password authentication enabled or disabled on the server to which you are attempting to connect?

---

### Post by Naatan on 2008-04-26
Nevermind, I figured it out.

The log showed:

User nagios from xxx.xxx.xxx.xxx not allowed because not listed in AllowUsers

So I checked the ssh config file at "/etc/ssh/sshd_config" and found added:

AllowUsers nagios

Reloaded sshd and now it works *sigh*

Thanks anyway ;)

---

