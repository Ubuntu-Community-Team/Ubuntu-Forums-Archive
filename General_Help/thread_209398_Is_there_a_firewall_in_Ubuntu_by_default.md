---
title: "Is there a firewall in Ubuntu by default??"
date: 2006-07-05
forum: General Help
---

### Post by AlliumPorrum on 2006-07-05
Hi!

I have installed Ubuntu 6.06, and for a few days I have being trying to get the MySQL Administration tool to work. I'm running that tool in my Win XP laptop, and want to connect with it to my Ubuntu server running the MySQL. But it won't work, I'm just getting this "connection cannot be established" error all the time. So the question is: is there some sort of software firewall installed on ubuntu by default?? I mean that is it possible that my server's firewall is blocking the connection to the port 3306??

---

### Post by mlind on 2006-07-05
Yes there is, IPTABLES, but it doesn't have any rules by default. In other words, it's not enabled.

---

### Post by ajgreeny on 2006-07-05
In fact you're unlikely to really need a firewall as no ports are open by default in Ubuntu.  Firestarter is worth looking at if you feel you want to have a front end to iptables, but it isn't really necessary.  Certainly there is nothing in this respect that would be causing your problem.

---

### Post by AlliumPorrum on 2006-07-05
Ok, so maybe Win XP SP2's own firewall is blocking the connection from the client side then... Have to check that when I get home.

Thanks!

---

### Post by ajgreeny on 2006-07-05
Win XP's firewall couldn't be affecting your Dapper system unless somehow the win Fwall has permanently changed a hardware router firewall you pass through in all booted systems.  The win Fwall won't be running when you boot to Ubuntu.

---

### Post by lamego on 2006-07-05
The default from mysql server is to be binding to localhost (127.0.0.1), this means it will only accept connections from local applications. 
To change that, edit /etc/mysql/my.cnf and comment out the line
bind-address = 127.0.0.1:
Then you will need to restart the mysql server with:
```
/etc/init.d/mysql restart
```

---

### Post by AlliumPorrum on 2006-07-05
I meant that maybe the XP's (=client) firewall is somehow blocking the connection between it and my Ubuntu/MySQL server. I don't know if a firewall in client machine really can do this or not, but what else can there be?? Both machines are anyway on my own WLAN network, so there is not any hardware firewalls between them.

Or is there something that I should know about using server ports in Ubuntu...? After living a few weeks with Linux, I've noticed that there is ALWAYS some strange config file somewhere, and you must know exactly how to edit it before anything works...;)

---

