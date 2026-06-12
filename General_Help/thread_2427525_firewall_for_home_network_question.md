---
title: "firewall for home network question"
date: 2019-09-23
forum: General Help
---

### Post by Old Jimma on 2019-09-23
Hi Ubuntuerainians and Ubuntuettes!!

i have a home network with 3 computers:
[LIST=1]
[*]a "server" with lots of hard disk space running Ubuntu 18.04
[*]a Lenovo laptop running Ubuntu 18.04, and
[*]a raspberry pi running the latest raspian.
[*]
[/LIST]

The laptop and raspberry pi computers have read-only access to 

Folders on the "server" are accessed by the  laptop and raspberry pi computers using NFS. The pi and lenovo computers have read-only privileges.

Also, the pi machine can be accessed using Remina RDP from both the "server" and the laptop.

_After loosing my identity several times for no fault of my own, I came the to conclusion that I want to protect my home computers and network._

I tried installing GUFW.... seemed nice and simple, but could not figure out the "rules" to add to each machine to make it work.... and during this experimentation, neither the pi or laptop could access my server.

Can someone suggest how to procede to add more security either with GUFW or iptables? 

I'm a geezer and have been running Ubuntu since around 2008 and spent alot of time in the early years getting my machines to work. I'm a geezer now and don't want to spend the rest of what is left in my live working on this.... and  hope to have a simple solution. I can follow instructions!! Things that a re simple and work are best for me!!

I'll be so grateful for your patience and advice. If you want to give me step by step directions, I'm good for a coffee the next time you are in town!

Gratefully!
Old Old Old Old Old Jimma from the Old Country

---

### Post by TheFu on 2019-09-23
Every computer should be running a firewall. Each needs to configure have the firewall configured locally.  There's no way you can use a firewall on a Linux desktop to protect a raspberry-pi from the internet or some other desktop.

You should also have a router that also runs a firewall, probably blocking all inbound requests and many outbound requests.  For this device, it is important that the router firmware be upgraded every month with patches.  If the vendor doesn't provide updates at least quarterly, check whether the device is still supported. Might need a new router or need to find some after-market firmware to use, which is updated monthly.

---

### Post by SeijiSensei on 2019-09-23
I have no firewalls on any computer behind my two routers.

---

### Post by oldrocker99 on 2019-09-23
Here's what to do:
```
sudo ufw enable
```

It will return```
firewall is enabled and added to startup
```
Or words to that effect.

---

### Post by ank2 on 2019-09-23
In my opinion you don't need a firewall, unless you want to provide certain serivices to some users. If you don't run any services you don't need to take care using a firewall.

---

### Post by TheFu on 2019-09-23
> **ank2 said:**
> In my opinion you don't need a firewall, unless you want to provide certain serivices to some users. If you don't run any services you don't need to take care using a firewall.

He's running NFS!  That's a service. He needs a WAN firewall and on the LAN, so when NFS is misconfigured or the local firewall is misconfigured, it isn't open to the world.  Layered security is needed for normal people.

---

### Post by uRock on 2019-09-23
> **TheFu said:**
> He's running NFS!  That's a service. He needs a WAN firewall and on the LAN, so when NFS is misconfigured or the local firewall is misconfigured, it isn't open to the world.  Layered security is needed for normal people.

+1 Definitely needed when running services. I have all of my devices on one network and don't want any of the "smart" devices accessing my Motion camera streams. Back when I ran it as "just a desktop," I still enabled UFW.

---

### Post by Old Jimma on 2019-09-24
Jeepers!!

I am grateful for the spirited replies!!!

I will start by enabling a firewall for my ubuntu "server."

**NFS is already set up and working and allows the laptop and raspberry pi to access certain folders on my ubuntu servers. The goal of using ufw is to make sure that nobody else can access files on the server other than the laptop and raspberry pi.**

Please review my rules to see if I've specified the correct ufw rules below!

1. I'll enable NFS: **# ufw enable nfs**

2. Then allow for my laptop: **#ufw allow from 192.168.1.71 to any port 80 proto nfs**

3. And, allow for my raspberry pi: **#ufw allow from 192.168.1.98 to any port 80 proto nfs**

**Do these commands achieve my goal?**

(I really don't know why I should use port 80 rather than any other port. Can someone comment on this?)

Thanks,
Old JImma

---

### Post by TheFu on 2019-09-24
I don't think this does what you want.
We need to see
```
sudo ufw status 
```
output.

---

### Post by Old Jimma on 2019-09-24
Here is the results from doing a> sudo ufw status:


> sudo: ufw: command not found


Old Jimma

---

### Post by uRock on 2019-09-24
Are your running as root? try **ufw status**

---

### Post by TheFu on 2019-09-24
Well, if you can't run ufw, then you certainly don't have any settings configured.

---

### Post by Old Jimma on 2019-09-24
Hi Fu:

I ran xman, and didn't get too far. Hope you'll notice that I've responded to query. I know you are busy!

Jimma

---

### Post by uRock on 2019-09-24
Did you by chance uninstall ufw at some point? I set myself as root and ran it with sudo and still had results. With ufw disabled, I still get an output.

---

### Post by TheFu on 2019-09-24
I don't know how to explain xman. It is self explanatory to me. But this thread isn't about xman.

If you've been here since 2006, seems that *command not found* would be a trivial problem to fix.
```
$ sudo ufw status
Status: active

To                         Action      From
--                         ------      ----
22/tcp                     ALLOW       Anywhere                  
Anywhere                   DENY        103.206.0.0/16
```
is what it returns on my laptop.  It is an NFS client. My ufw setup is **default DENY** for inbound but allows any outbound. NFS outbound, as a client, doesn't need any rule.  In theory, that 2nd DENY rule shouldn't be needed.  Someone from that subnet was trying to hack my machine. through ssh on port/22.  It was automatically blocked because I use fail2ban, but I didn't want to take any chances after I looked up where the subnet was located.

---

### Post by SeijiSensei on 2019-09-24
Was this on a client machine with no Internet-facing adapters behind a firewall? How did a connection from 103.206 ever reach this machine?

I run NFS on a server that's behind two firewall routers.  It's never "misconfigured" since the contents of /etc/exports only includes local LAN addresses in private, unrouted address blocks. It's also pretty hard to misconfigure a standard wifi router. Usually you plug it in, and it blocks everything on its WAN side by default.

---

### Post by SeijiSensei on 2019-09-24
> **Old Jimma said:**
> 2. Then allow for my laptop: **#ufw allow from 192.168.1.71 to any port 80 proto nfs**

(I really don't know why I should use port 80 rather than any other port. Can someone comment on this?)

Port 80 is assigned to HTTP.  It would never be a target for NFS packets.  NFS uses port 2049.  Look at the contents of /etc/services to see how ports are assigned.

I don't know what "proto" means in UFW.  In the standard iptables rules that UFW generates, protocols are things like TCP, UDP, and ICMP, not services like NFS.  If you want to permit NFS connections, the iptables rules would read:
```

/sbin/iptables -I INPUT -s 192.168.1.71 -p tcp --dport 2049 -j ACCEPT
/sbin/iptables -I INPUT -s 192.168.1.71 -p udp --dport 2049 -j ACCEPT

```
Usually NFS uses UDP, but sometimes TCP is used instead.

---

### Post by Old Jimma on 2019-09-24
Hi Folks:

I learned that a family member got a very bad medical prognosis. I'll be traveling for the next few days to visit and will return the the forums to learn more next week. My sincerely thanks for your suggestions and help.

Old Jimma

---

### Post by uRock on 2019-09-24
Thanks for the heads up. Safe travels and wishing you and your's the best!

---

