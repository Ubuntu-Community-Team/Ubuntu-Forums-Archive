---
title: "ssh to remote server"
date: 2015-04-15
forum: General Help
---

### Post by ELMIT on 2015-04-15
If something goes wrong, then it really goes wrong  - sigh !!!!


I got a remote site with digitalocean. Works fine!
I secured the site with fail2ban and white listed my own IP.

At the beginning I played around with the remote site and "checked" if I can get also graphic to work there with VNC. I could. I never used it anymore, and forgot about it.

Now I moved. With that my IP address changed. I also got a new router.
At the same time my hard disk cannot be read anymore and I installed a new 14.04.2 system

As it must be, I mis-spelled my password when I tried to login with ssh. Tied setup of fail2ban allows only 2 login attempt and then locks me out for 60 (!!!!) days.

No problem, use the digital ocean console and log in. 
Now VNC kicks in and I can not see anything. The font is all colors and the mouse courser is off by half the screen.
I managed to white list my new IP address in fail2ban, restarted fail2ban. I tried to drop 
fail2ban-client set ssh-iptables unbanip <new IP>
Hardly to read, it said, that this IP is not banned.

Though, when I try to use ssh to the server from my desktop I get with ssh [email]user@remote.server[/email]
ssh_exchange_identification: read: Connection reset by peer

If I try to ssh multiple times, I do not get the fail2ban email that I am locked out. It seems, whitelisting worked.

What do you suggest me to do?

---

### Post by mastablasta on 2015-04-16
can you use the Ocean's console to check the logs? if so, check security.log to see what is happening.

also it is recommended to use keys instead of passwords. one advantage: you can't misstype :P

in VNC - can you drop to terminal (ctrl+alt+F1)?

---

### Post by ELMIT on 2015-04-16
I can log in with VNC of digitalocean, but I can hardly see something. Where is "security.log" ?

How can I use KEYs instead password (now)?
E.g. can I put the key onto the website and retrieve it? (hoping that during that minute not a hacker watches my download)

Or how can I use VNC from my desktop? I remember I had to set something on the server (password), ...

I tried CTRL-ALT-F1, but that made my screen blank and switched my local machine to terminal 1 --- GRRRR!!!

---

### Post by ELMIT on 2015-04-16
Found it!

I had secured the site with an entry in /etc/hosts.allow 
sshd: <my old IP>

after changing it to my new IP and restarting ssh I can login.

Thanks for listening ;-)

---

### Post by Lars Noodén on 2015-04-16
> **ELMIT said:**
> I had secured the site with an entry in /etc/hosts.allow

Glad you found it.  Ubuntu 14.04 is on OpenSSH 6.6 which still supports tcpwrappers. 

In later versions, specifically 6.7 and onwards, [tcpwrappers are no longer supported](http://www.openssh.com/txt/release-6.7) in OpenSSH.  So you might consider clearing out hosts.allow and hosts.deny and move the restrictions to iptables/ufw to future-proof the host.  UFW (frontend for iptables) can restrict incoming connections by source ip and even limit the rate of new connections.

---

