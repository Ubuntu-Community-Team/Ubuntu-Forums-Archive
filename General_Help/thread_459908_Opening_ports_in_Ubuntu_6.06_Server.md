---
title: "Opening ports in Ubuntu 6.06 Server"
date: 2007-05-31
forum: General Help
---

### Post by jamilb on 2007-05-31
Hi,

I'm trying to set up an old machine as a server for a mysql database that will be accessed by a website hosted on a different machine. I've installed Ubuntu 6.06 server, and have copied my database over. However, I can't seem to make an connections with the server. I'm assuming this is because Ubuntu server comes with all ports closed by default, so I would need to specifically open some. 

Specifically, I need my PHP-based website to be able to query and update the database, and I also need to be able to ssh to the computer and copy files etc... Can someone tell me how I can do this? I've tried googling the answer, but can't seem to get it to work. I only have basic knowledge of linux.

Many thanks

Jamil

---

### Post by beatbros on 2007-05-31
> **jamilb said:**
> Hi,

I'm trying to set up an old machine as a server for a mysql database that will be accessed by a website hosted on a different machine. I've installed Ubuntu 6.06 server, and have copied my database over. However, I can't seem to make an connections with the server. I'm assuming this is because Ubuntu server comes with all ports closed by default, so I would need to specifically open some. 

Specifically, I need my PHP-based website to be able to query and update the database, and I also need to be able to ssh to the computer and copy files etc... Can someone tell me how I can do this? I've tried googling the answer, but can't seem to get it to work. I only have basic knowledge of linux.

Many thanks

Jamil

Hi,
maybe your firewall is turned on and block every incoming connection.

if you issue this command you can view your configuration:
```

sudo iptables -L

```

if you see that all connections are granted the output should be like this:

Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination    

Probably in your configuration there will be some (or all) rules that drop connections.

if this is the case you can:
stop the firewall completely and see if connections can be made.
reconfigure the firewall with the ports you need.
A Suggested Tool for a smart firewall configuration - > Firestarter

Bye

---

### Post by jamilb on 2007-05-31
Hi, thanks for the rapid response!

The output is as you said, although there is an extra line under the CHAIN INPUT line that reads as follows:

TCP -- ANYWHERE                          ANYWHERE                           TCP DPT:SSH

How can I make sure my firewall is off through iptables? I can't seem to get firestarter to install (it claims it can't find it through apt-get), and in any case would it even work on Ubuntu server, given that there is no GUI at all?

Thanks

Jamil

---

### Post by beatbros on 2007-05-31
ah Ok no GUI :D,
so it's a standard firewall config with ssh enabled.
Can you post your output of
```
sudo iptables -L
``` ?

Can you confirm that in this file:
/etc/mysql/my.cnf
you have commented the localhost-only listening address ?

relevant line:
bind-address = 127.0.0.1

should be:
#bind-address = 127.0.0.1

restart mysql with
```
sudo /etc/init.d/mysql restart
```

now should listen to the ip address in LAN.

I assume that you are running Apache on port 80....

then from the other PC  you have to try :

telnet linuxbox_ipaddr 22
telnet linuxbox_ipaddr 80
telnet linuxbox_ipaddr MYSQLPORT(check in your config file)

if the 3 telnet above are in a connected state you are ok , if they hangs till timeout you are still firewalled...

---

