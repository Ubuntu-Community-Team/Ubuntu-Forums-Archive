---
title: "unable to connect via tcp/ip to mysql -- sockets and terminal conneciton work fine"
date: 2013-11-07
forum: General Help
---

### Post by wendallsan on 2013-11-07
Hi all,

Fresh install of Ubuntu 13.10, ran 'sudo apt-get install lamp-server^' to set it up as a LAMP server.  Installed mySQL Workbench and tried to connect to localhost as root (hostname: 127.0.0.1, port: 3306, username: root, password: [root password], default schema: test).  Got the error :

"Failed to Connect to MySQL at 127.0.0.1:3306 with user root
Can't connect to MySQL server on '127.0.0.1' (111)"

I have confirmed that mysqld is running, and that the server is configured to listen on port 3306 (I have not altered the default my.conf file).

I have allowed port 3306 in iptables, here is the output of 'iptables -L':

```

Chain INPUT (policy ACCEPT)
target     prot opt source               destination         
ACCEPT     tcp  --  anywhere             anywhere             tcp dpt:mysql

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination     

```    

I am able to connect if I set up a connection using the mysql socket rather than TCP, and I am able to connect through the terminal with the 'mysql' command.  I am completely unable to connect via TCP from either the localhost or a remote system.  I've done this before on many servers and this has worked fine out of the box.  Can anyone tell my what I've done wrong and why I cannot connect via TCP to mySQL?  Thanks for any help.

---

### Post by SeijiSensei on 2013-11-08
Do you have a user called 'root'@'%' or 'root'@'client-ip-address' in MySQL?  

If you are trying to connect to an interface other than 127.0.0.1, you need to tell MySQL to listen on all interfaces.  In my.cnf, you need
```
bind-address    = 0.0.0.0
```.

---

### Post by wendallsan on 2013-11-12
Thanks!  As son as I set the bind-address to 0.0.0.0 in my.cnf I was immediately able to connect via MySQL workbench on the local system, and after adding 'root'@'%' I was able to connect from other clients on my network.  This is exactly what I needed, and I've taken notes on what was needed so I hopefully won't be back here again asking the same question next time I set up another Ubuntu server.  Once more, thanks very much for your help, you were dead on!

---

