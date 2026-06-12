---
title: "unable to ssh to ubuntu machine"
date: 2007-11-12
forum: General Help
---

### Post by pcrew on 2007-11-12
I have been able to ssh to this box in the past however after some recent updates of all the latest packages for ubuntu fiesty release i am unable to ssh to my box from my laptop connected to the same switch as my ubuntu box.

- i am able to ssh on the localhost
- i have tried ssh [email]user@ip.addr[/email]ess and get Operation timed out error.
- i have no fire wall and no iptables.
output of iptables -nL

~# iptables -nL
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         


output of netstat -tnl

~# netstat -tnl
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State      
tcp        0      0 127.0.0.1:2208          0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:773             0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:111             0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:80              0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN     
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN     
tcp        0      0 127.0.0.1:2207          0.0.0.0:*               LISTEN    


sshd_config

# What ports, IPs and protocols we listen for
Port 22

# Use these options to restrict which interfaces/protocols sshd will bind to
#ListenAddress ::

ListenAddress 0.0.0.0
Protocol 2
# HostKeys for protocol version 2
HostKey /etc/ssh/ssh_host_rsa_key
HostKey /etc/ssh/ssh_host_dsa_key
#Privilege Separation is turned on for security
UsePrivilegeSeparation yes



any assistance in resolving this is highly appreaciated

---

### Post by cmnorton on 2007-11-12
Sorry, I see sshd is running from re-looking at your post.

---

### Post by dacap06 on 2007-11-12
It looks like you have covered the situation on your server fairly thoroughly.  The only thing on the server I would ask you to check is that the thing that is listening to port 22 on your server is really sshd.  The easy way to do that is ps -aef | grep /usr/sbin/sshd | grep -v grep.  If you see output, it's running.

The only other thing I can think of is this:  have you checked to make sure the firewall on your laptop allows your ssh client out?  Can you ssh from your laptop to anything else?

DaCAP

---

### Post by qpieus on 2007-11-12
in my sshd_config, the```
ListenAddress 0.0.0.0
```line is commented out. I see yours is not commented out. Since yours is not commented, does that mean it'll only listen to 0.0.0.0? Try commenting that line out.

If you do comment out that line then restart ssh by doing:

sudo /etc/init.d/ssh restart

---

### Post by pcrew on 2007-11-12
DACAP
I tried the grep command and it shows output and shows sshd is running.


qpieus
i have commented and commented out the Listen line and that does not seem to make any difference.

I am able to ssh to other machines on my network.

i am able to ssh to locahost on port 22 on the ubuntu machine itself however i am unable to ssh from any other machine on the network to the ubuntu box in question.

---

### Post by AlexThomson_NZ on 2007-11-12
Can you SSH to it using it's IP address?

Also, another thing it could be (unlikely but I have encountered it at work) is if the openssh versions differ too greatly

---

### Post by pcrew on 2007-11-13
:mad:    

i finally found the problem. since i recently moved offices, my network team had connected the wrong ethernet interface on the ubuntu box and hence i was unable to ssh or ping to the box on the primary ip address.

---

### Post by qpieus on 2007-11-13
jeez, I almost asked in my prior post "are you sure you have the right IP address?" I guess I should have!

---

