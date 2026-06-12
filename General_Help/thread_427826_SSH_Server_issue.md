---
title: "SSH Server issue"
date: 2007-04-29
forum: General Help
---

### Post by oplekv2 on 2007-04-29
I'm running out of ideas for solving this, so here I go.

Simply put, I am trying to set up a SSH server.  It's up and running, but I can't connect from outside my router/hub.

The server machine can connect through loopback.
The server machine can connect through its own LAN IP.
A fellow machine in the LAN can also connect through its LAN IP.

Nothing can connect to my outer IP (assigned by my ISP).

Before you say "well duh!", I understand the router must be set properly, and I do have mediocre experience with this.

The port is forwarded (both 22 and my special 7777).  External sources doing a port scan on me say the port (7777) is open, and it appears to be running a service.

I've successfully forwarded ports in the past, so I'm not totally inept.

The best I can figure is that the SSH daemon is set to only allow connections from its local domain.  But I can't see anything in the sshd_config file that indicates this.

Any wisom out there?

Thanks

My sshd config file (distilled)

```
Port 7777
Protocol 2
HostKey /etc/ssh/ssh_host_rsa_key
HostKey /etc/ssh/ssh_host_dsa_key
UsePrivilegeSeparation yes
KeyRegenerationInterval 3600
ServerKeyBits 768
SyslogFacility AUTH
LogLevel INFO
LoginGraceTime 120
PermitRootLogin yes
StrictModes yes
RSAAuthentication yes
PubkeyAuthentication yes
IgnoreRhosts yes
RhostsRSAAuthentication no
HostbasedAuthentication no
PermitEmptyPasswords no
ChallengeResponseAuthentication yes
X11Forwarding yes
X11DisplayOffset 10
PrintMotd no
PrintLastLog yes
TCPKeepAlive yes
UseLogin yes
AcceptEnv LANG LC_*
Subsystem sftp /usr/lib/openssh/sftp-server
UsePAM yes

```

---

### Post by steve0921 on 2007-04-29
There is nothing wrong with your sshd configuration; it is identical to mine and I can ssh in from outside.

Unfortunately, I can only tell you that this isn't your problem. I can't say for sure what is. Have you installed or reconfigured any firewalls? The default supplied ones with their original configurations should allow outside connections (anecdotally). If there are any other servers running on the computer (web, ftp, etc.) do they have similar issues?

What is the error ssh gives?

---

### Post by oplekv2 on 2007-04-30
The failed attempts only say that the connetion was refused.

I reinstalled the OS only a few weeks ago, and haven't added anything weird.  I just know it's been successfully done before.

I shut off the router's firewall completely to no effect.

I seem to remember hearing some weirdness that some routers have about connections to internal computers.  I'm going to try from work (outside) and see if it isn't something like that.

---

### Post by lakersforce on 2007-04-30
Sometimes you will have to use the modem provided by your ISP provider. Use of a different modem is known to cause problems. Try to run a NMAP on your computer, both from within the computer and from outside. You should then be able to see if your ports are open to outsiders. Your ports can look open when you run it from your own computer, but it is not when an computer from the outside looks at it.

---

### Post by oplekv2 on 2007-04-30
I am using my ISP's modem, but I almost wonder if Verizon isn't blocking *all* incoming ports, except a specific few.  That's why I tried for port 7777 in the first place.

Thanks for the nmap suggestion.  I didn't know that one.  IT says 7777 is closed (with router firewall on and off).  I've gone over the router with a fine-toothed comb.  I'm not sure how I can be screwing that part of it up.

I still can't find any installed firewalls on this comp.  Traceroute doesn't seem to help me from my location, but maybe externally I can gather where it dies.

---

### Post by firebadger on 2007-04-30
Some routers disconnect on idle by default.  My 3com one did and it caused me a lot of grief before I figured it out.
However, this is unlikely to be the case unless you only try your remote tests after being idle at home for some time.

---

### Post by steve0921 on 2007-04-30
I do hear some nasty things about Verizon, though I don't know if they would actually block random higher ports.

Have you tried using port 22 just to see if it works?

Also, can you temporarily connect the computer directly to the modem without using the router? This would tell you whether it's an ISP or router issue.

---

### Post by oplekv2 on 2007-04-30
> **steve0921 said:**
> I do hear some nasty things about Verizon, though I don't know if they would actually block random higher ports.

Have you tried using port 22 just to see if it works?

Also, can you temporarily connect the computer directly to the modem without using the router? This would tell you whether it's an ISP or router issue.

The modem is the router.  One of those combo deals.

I have the answer, actually.  People can connect from outside my router's LAN.  I just can't connect to that outer IP from inside.. which isn't a big deal really, since I can connect to internal IP fine.

So in short, there's no problem.  It's all in my head.  That, and a weird modem.

---

### Post by silverbullet007 on 2007-05-01
Are you using any sort of Dynamic DNS for resolution?  If for example, your trying to hit your home machine from across the internet then unless you paid for a static IP you wont be able to without DDNS...and even with a static it might not be a public static.

---

