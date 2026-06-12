---
title: "Questions about Iptables"
date: 2016-08-17
forum: General Help
---

### Post by sebastiaan5 on 2016-08-17
Hello,

I have a server running and I want to set up Iptables, but I don't understand it fully how to save rules.

I followed a guide and it said make a file "/etc/iptables.firewall.rules" I googled a lot and I got very strong rules (I think, if something is not correct please tell me):

```


*filter

#  Allow all loopback (lo0) traffic and drop all traffic to 127/8 that doesn't use lo0
-A INPUT -i lo -j ACCEPT
-A INPUT -d 127.0.0.0/8 -j REJECT

#  Accept all established inbound connections
-A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT

#  Allow all outbound traffic - you can modify this to only allow certain traffic
-A OUTPUT -j ACCEPT

#  Allow HTTP and HTTPS connections from anywhere (the normal ports for websites and SSL).
-A INPUT -p tcp --dport 80 -j ACCEPT
-A INPUT -p tcp --dport 443 -j ACCEPT

#  Allow DNS
-A OUTPUT -p udp -m udp --dport 53 -j ACCEPT

#####################MAIL SERVER#####################
#not in use
#
# Allows SMTP access
#-A INPUT -p tcp --dport 25 -j ACCEPT
#-A INPUT -p tcp --dport 465 -j ACCEPT
#-A INPUT -p tcp --dport 587 -j ACCEPT
#
# Allows pop and pops connections
# -A INPUT -p tcp --dport 110 -j ACCEPT
# -A INPUT -p tcp --dport 995 -j ACCEPT
#
# Allows imap and imaps connections
#-A INPUT -p tcp --dport 143 -j ACCEPT
#-A INPUT -p tcp --dport 993 -j ACCEPT
#
#####################MAIL SERVER#####################

#Block mysql other then 192.168.0.0
-A INPUT -p tcp -s 192.168.0.0/24 --dport 3306 -m state --state NEW,ESTABLISHED -j ACCEPT

#Allow SSH connections
#The -dport number should be the same port number you set in sshd_config
-A INPUT -p tcp -m state --state NEW --dport 22 -j ACCEPT
-A OUTPUT -o eth0 -p tcp --dport 22 -m state --state NEW,ESTABLISHED -j ACCEPT

#Allow ping
-A INPUT -p icmp --icmp-type echo-request -j ACCEPT

#SMURF attack protection
-A INPUT -p icmp -m icmp --icmp-type address-mask-request -j DROP
-A INPUT -p icmp -m icmp --icmp-type timestamp-request -j DROP

# Droping all invalid packets
-A INPUT -m state --state INVALID -j DROP
-A FORWARD -m state --state INVALID -j DROP
-A OUTPUT -m state --state INVALID -j DROP

#Flooding of RST packets, smurf attack Rejection
-A INPUT -p tcp -m tcp --tcp-flags RST RST -m limit --limit 2/second --limit-burst 2 -j ACCEPT

#Protecting portscans
#Attacking IP will be locked for 24 hours (3600 x 24 = 86400 Seconds)
-A INPUT -m recent --name portscan --rcheck --seconds 86400 -j DROP
-A FORWARD -m recent --name portscan --rcheck --seconds 86400 -j DROP

#Remove attacking IP after 24 hours
-A INPUT -m recent --name portscan --remove
-A FORWARD -m recent --name portscan --remove

#These rules add scanners to the portscan list, and log the attempt.
-A INPUT -p tcp -m tcp --dport 139 -m recent --name portscan --set -j LOG --log-prefix "portscan:"
-A INPUT -p tcp -m tcp --dport 139 -m recent --name portscan --set -j DROP

-A FORWARD -p tcp -m tcp --dport 139 -m recent --name portscan --set -j LOG --log-prefix "portscan:"
-A FORWARD -p tcp -m tcp --dport 139 -m recent --name portscan --set -j DROP

#Block bad ports
-A INPUT -p tcp -m multiport --dport 135,136,137,138,139,445 -j DROP
-A INPUT -p udp -m multiport --dport 135,136,137,138,139,445 -j DROP

#Block DDoS
#maximum 25 connection per minute
-A INPUT -p tcp --dport 80 -m limit --limit 25/minute --limit-burst 100 -j ACCEPT
-A INPUT -p tcp --dport 443 -m limit --limit 25/minute --limit-burst 100 -j ACCEPT

#Log iptables denied calls
-A INPUT -m limit --limit 5/min -j LOG --log-prefix "iptables denied: " --log-level 7

#Drop all other inbound - default deny unless explicitly allowed policy
-A INPUT -j DROP
-A FORWARD -j DROP

COMMIT

```

To save the rules I just need to type:

```
sudo iptables-restore < /etc/iptables.firewall.rules
```

To enable on boot:

```
sudo nano /etc/network/if-pre-up.d/firewall

##########script begin#########
#!/bin/sh
/sbin/iptables-restore < /etc/iptables.firewall.rules
##########script end#########

sudo chmod +x /etc/network/if-pre-up.d/firewall
```

So I'm wondering is it really saved by just copying lines from a file to iptables-restore. Don't I need to tell systemd or the kernel or something else?

I found another guide that says you can install iptables-persistent and to save iptables I need to:

```
service netfilter-persistent save
```

Which I think is more persistent and correct?
How do I check if my Iptables are active and saved? Just by doing iptables -L and look if all is there?


greetings

---

### Post by sebastiaan5 on 2016-08-19
bump

---

### Post by Doug S on 2016-08-19
There are several ways to do iptables stuff.

> **sebastiaan5 said:**
> To save the rules I just need to type:

```
sudo iptables-restore < /etc/iptables.firewall.rules
```

Most of us normally call that "loading the rule set" as opposed to saying "save the rules". Myself, I found it confusing to read.

> **sebastiaan5 said:**
> To enable on boot:

```
sudo nano /etc/network/if-pre-up.d/firewall

##########script begin#########
#!/bin/sh
/sbin/iptables-restore < /etc/iptables.firewall.rules
##########script end#########

sudo chmod +x /etc/network/if-pre-up.d/firewall
```Well, I've never seen that method before, so add yet another method.

> **sebastiaan5 said:**
> So I'm wondering is it really saved by just copying lines from a file to iptables-restore. Don't I need to tell systemd or the kernel or something else?The "iptables-restore command loads the iptables rule set from the file. Required kernel modules will be loaded as a result and you should be ready to go.

> **sebastiaan5 said:**
> I found another guide that says you can install iptables-persistent and to save iptables I need to:

```
service netfilter-persistent save
```

Which I think is more persistent and correct?Yes, I have seen this stuff, and a great many people recommend it. Myself, I don't understand. Why use some additional package to do something that is so trivial in the first place. (but I am a server person and avoid anything extra.)

> **sebastiaan5 said:**
> How do I check if my Iptables are active and saved [loaded]? Just by doing iptables -L and look if all is there?

Yes. Myself, I like to look at the packet and byte counters and not do lookups, so I do "sudo iptables -v -x -n -L" and "sudo iptables -t nat -v -x -n -L". You can also use "sudo iptables-save -c"

I do use a script for my iptables rule set, because I also do some other, but directly related things. I load it on startup via the interfaces file:

```
doug@DOUG-64:~$ cat /etc/network/interfaces
# interfaces file for smythies.com 2016.01.30
#       attempt to set local DNS herein, as the method
#       used with the old 12.04 server no longer works.
#
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback
[COLOR="#FF0000"]pre-up /home/doug/init/doug_firewall[/COLOR]
dns-nameservers 127.0.0.1

# The primary interface (d-link PCI card)
auto enp4s0
iface enp4s0 inet dhcp

# Local network interface (uses built in ethernet port)
auto enp2s0
iface enp2s0 inet static
  address 192.168.111.1
  network 192.168.111.0
  netmask 255.255.255.0
  broadcast 192.168.111.255

```Using the interfaces file method, you wouldn't need a script, just execute the iptables-restore load command directly.

---

### Post by &amp;KyT$0P# on 2016-08-19
I just put in /etc/rc.local, before the [FONT=Courier New]exit 0[/FONT] line
```
cat /etc/iptables.firewall.rules | iptables-restore
```

---

### Post by sebastiaan5 on 2016-08-20
I get it now, thank you both for the response.

---

