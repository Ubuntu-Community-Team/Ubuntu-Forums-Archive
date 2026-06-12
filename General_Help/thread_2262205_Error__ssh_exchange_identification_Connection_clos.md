---
title: "Error:  ssh_exchange_identification: Connection closed by remote host"
date: 2015-01-23
forum: General Help
---

### Post by robfindlay on 2015-01-23
So out of the blue I am unable to SSH into one of my Ubuntu boxes.  Ubuntu Desktop 14.04

The only customization I made was moving the connection port to 443. Everything was working fine for weeks. 

Then out of the blue: I get this when trying to connect from ANY host. 

```
ssh -vv -p 443 slag@ri3.chickenkiller.com
OpenSSH_6.2p2, OSSLShim 0.9.8r 8 Dec 2011
debug1: Reading configuration data /etc/ssh_config
debug1: /etc/ssh_config line 20: Applying options for *
debug1: /etc/ssh_config line 102: Applying options for *
debug2: ssh_connect: needpriv 0
debug1: Connecting to ri3.chickenkiller.com [76.27.95.54] port 443.
debug1: Connection established.
debug1: identity file /Users/rfindlay/.ssh/id_rsa type 1
debug1: identity file /Users/rfindlay/.ssh/id_rsa-cert type -1
debug1: identity file /Users/rfindlay/.ssh/id_dsa type -1
debug1: identity file /Users/rfindlay/.ssh/id_dsa-cert type -1
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_6.2
debug1: ssh_exchange_identification: \025
ssh_exchange_identification: Connection closed by remote host
```

Or, 

```
ssh -vv -p 443 slag@ri3.chickenkiller.com
OpenSSH_6.6.1, OpenSSL 1.0.1f 6 Jan 2014
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: /etc/ssh/ssh_config line 19: Applying options for *
debug2: ssh_connect: needpriv 0
debug1: Connecting to ri3.chickenkiller.com [76.27.95.54] port 443.
debug1: Connection established.
debug1: identity file /home/rob/.ssh/id_rsa type -1
debug1: identity file /home/rob/.ssh/id_rsa-cert type -1
debug1: identity file /home/rob/.ssh/id_dsa type -1
debug1: identity file /home/rob/.ssh/id_dsa-cert type -1
debug1: identity file /home/rob/.ssh/id_ecdsa type -1
debug1: identity file /home/rob/.ssh/id_ecdsa-cert type -1
debug1: identity file /home/rob/.ssh/id_ed25519 type -1
debug1: identity file /home/rob/.ssh/id_ed25519-cert type -1
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_6.6.1p1 Ubuntu-2ubuntu2
debug1: ssh_exchange_identification: \025
ssh_exchange_identification: Connection closed by remote host
```

I CAN connect if I ssh into another box on the network and then ssh from IT to the troublesome box by local IP. 

My hosts.deny and hosts.allow are stock, zero entries. 

The .ssh folders are chmod 700 & 600 respectively. 

I did a bit of searching and lots of folks have had this problem and the only fix I've seen is a complete reinstall of openssh

I'm hoping to avoid that if at all possible. 

I'm at a loss! 

Any thoughts? 

Thanks. 

-Rob

---

### Post by robfindlay on 2015-01-23
Arg!! I uninstalled the opehssh server  with prejudice, i.e. --purge. 

Reinstalled, exact same error.....

---

### Post by Lars Noodén on 2015-01-23
What really is listening on the server at port 443?

```

netstat -ntlp | grep 443

```

Do you have HTTPS already on port 443?  If so and you want to keep both HTTPS and SSH on the same port you will have to multiplex using [sslh](http://www.rutschle.net/tech/sslh.shtml).

---

### Post by robfindlay on 2015-01-23
> **Lars Noodén said:**
> What really is listening on the server at port 443?

```

netstat -ntlp | grep 443

```

Do you have HTTPS already on port 443?  If so and you want to keep both HTTPS and SSH on the same port you will have to multiplex using [sslh](http://www.rutschle.net/tech/sslh.shtml).

Not running any web services on this box. It is sitting in my routers DMZ though that never caused a problem before. 

Here's the requested code: 
```

tcp        0      0 0.0.0.0:443             0.0.0.0:*               LISTEN      1702/sshd
tcp6       0      0 :::443                  :::*                    LISTEN      1702/sshd

```

---

### Post by sandyd on 2015-01-23
What does the auth log on the computer you are sshing into contain? 

Also, are there any security systems installed that could cause this? (lfd/fail2ban/sshguard/etc)

---

