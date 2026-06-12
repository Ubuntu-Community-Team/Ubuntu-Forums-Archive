---
title: "How do you configure iptables to allow incoming traffic on specific ports"
date: 2013-02-06
forum: General Help
---

### Post by craig smith on 2013-02-06
I just installed some software that allows me to connect to other computers to remote control them. Problem is, I need to allow traffic on ports 8040 and 8041. I've already enabled port forwarding on my router to my server on these two ports but the utility used to check external accessibility says that the request was aborted. If I'm thinking right, out of the box ubuntu server comes with no rules to it's firewall allowing any connections. Is that correct? I've tried playing with rules in iptables to allow incoming connections on these ports, but nothing changes. Can someone point me in the right direction? I'm not sure what I'm missing here, it's probably something simple. Thanks in advanced for any help!

Craig

---

### Post by xianbei on 2013-02-06
First check to see what's open:

```
netstat -an | grep "LISTEN "
```

---

### Post by SeijiSensei on 2013-02-06
Install **nmap** from the repositories and start by seeing if the ports are open on the localhost interface by running "nmap localhost".  Now try the same thing from a machine outside your network.

---

### Post by 3rdalbum on 2013-02-06
You are correct, by default Ubuntu does not firewall any ports.

Are you behind a router? It will need configuring to allow those incoming ports. The same for the computers you want to control.

---

### Post by craig smith on 2013-02-07
Thanks for all the replies! 

@3rdalbum My router is configured to forward any incoming connections on these ports to the same ports on my server.

@xianbei ran your command and I see:

tcp   0  0 0.0.0.0.8040   0.0.0.0:*    LISTEN
tcp   0  0.0.0.0.0.8041   0.0.0.0:*    LISTEN

this means that my machine is listening on these ports, correct?

@SeijiSensei when I run the commant **sudo apt-get nmap** returned is E: Invalid operation **nmap**

---

### Post by craig smith on 2013-02-07
Does any one have any ideas?

---

### Post by SeijiSensei on 2013-02-07
You forgot to include the "install" command.

```
sudo apt-get **install** nmap
```

---

### Post by craig smith on 2013-02-07
@ SeijiSensei Thanks for fixing my brain fart! What does it mean if these two ports are not listed here? I can still access these ports form within the local network as the configuation web interface is still accessable. Thanks in advanced!

---

### Post by SeijiSensei on 2013-02-07
> **craig smith said:**
> @ SeijiSensei Thanks for fixing my brain fart! What does it mean if these two ports are not listed here? I can still access these ports form within the local network as the configuation web interface is still accessable. Thanks in advanced!

By default nmap checks a predetermined set of about 1,500 ports.  Maybe those are not included.  You can force it to look at specific ports like this:

```
nmap -p 8040-8041 localhost
```

---

### Post by craig smith on 2013-02-07
nmap says they are open... So my router is configured and the ports are open. It must be a problem with the software. Could my isp be blocking me? Just grabbing at straws now.

---

### Post by SeijiSensei on 2013-02-08
Are you sure you added exceptions to the router's firewall rules for those ports as well as setting up port forwarding?  Maybe they are still closed.

---

