---
title: "Run scripts at start..."
date: 2005-09-29
forum: General Help
---

### Post by camp on 2005-09-29
Hi all,

Sorry for writing one more thread on this topic. I haven't really found any answer to my little question.
I know that Debian based systems don't have an rc.local file, I'm totally ok with that too. But if I have a iptables script, that I want to start eveytime I boot my laptop... how do I do!?

I have read in some of the other threads, about making a /etc/init.d/ -start/stop script. The problem is... that I don't have a clue of how to make one! (At least not right now! ;) )...

Here is the script that I used to have running on my fedora box...
--- snip ---
#!/bin/sh

lo_if=lo
ext_if=eth0

#
# flush all rules
#
iptables -F
iptables -t nat -F

#
# set policy
#
iptables -P INPUT DROP
iptables -P OUTPUT ACCEPT
iptables -P FORWARD DROP

# allow all internal
iptables -A INPUT -i $lo_if -j ACCEPT
iptables -A OUTPUT -d 127.0.0.1 -j ACCEPT

# allow ping outbound...
iptables -A OUTPUT  -p icmp -j ACCEPT

# ssh
iptables -A INPUT -i $ext_if -p tcp --dport 22 -j ACCEPT
iptables -A OUTPUT  -p tcp --dport 22 -j ACCEPT


# http, https
iptables -A INPUT -i $ext_if -p tcp --dport 80 -j ACCEPT
iptables -A INPUT -i $ext_if -p tcp --dport 8080 -j ACCEPT
iptables -A INPUT -i $ext_if -p tcp --dport 443 -j ACCEPT
iptables -A OUTPUT -p tcp --dport 80 -j ACCEPT
iptables -A OUTPUT -p tcp --dport 8080 -j ACCEPT
iptables -A OUTPUT -p tcp --dport 443 -j ACCEPT

# allow VNC
iptables -A INPUT  -p tcp --dport 5900 -j ACCEPT
iptables -A OUTPUT  -p tcp --dport 5900 -j ACCEPT

# allow Yahoo
iptables -A INPUT  -p tcp --dport 5050 -j ACCEPT
iptables -A OUTPUT  -p tcp --dport 5050 -j ACCEPT

# allow MSN
iptables -A INPUT  -p tcp --dport 1863 -j ACCEPT
iptables -A OUTPUT  -p tcp --dport 1863 -j ACCEPT

# allow ICQ
iptables -A INPUT  -p tcp --dport 5190 -j ACCEPT
iptables -A OUTPUT  -p tcp --dport 5190 -j ACCEPT

# iWeather desklet
iptables -A INPUT -i $ext_if -p tcp --sport 34563 -j ACCEPT
iptables -A INPUT -i $ext_if -p tcp --dport 34563 -j ACCEPT

# established and related
iptables -A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT
iptables -A OUTPUT -m state --state ESTABLISHED,RELATED -j ACCEPT
--- snip ---

Thanks for all the help I can get!
/JC

---

### Post by davmac on 2005-09-29
The process for doing this is described at [http://ubuntu.wordpress.com/2005/09/07/adding-a-startup-script-to-be-run-at-bootup/](http://ubuntu.wordpress.com/2005/09/07/adding-a-startup-script-to-be-run-at-bootup/)

HTH,

Dave Mac

---

### Post by camp on 2005-09-29
Hi Davmac,

I will try this... and get back to you!

/JC

---

### Post by camp on 2005-10-02
Hi again!

It worked!!! Thanks for the help!

/JC

---

