---
title: "Cannot update due to Postgresql - CEST HINT:  Is another postmaster already running o"
date: 2013-06-18
forum: General Help
---

### Post by Gudjon on 2013-06-18
Hello!

Running Ubuntu 13.04 since it's release.
Suddenly I am having problem with Postgres, googled and tried out some suggestions for getting postgres right again - but failing :[INDENT]Setting up postgresql-common (140) ...
 * Starting PostgreSQL 9.1 database server                                                                                                 * The PostgreSQL server failed to start. Please check the log output:
2013-06-18 10:08:58 CEST LOG:  could not bind IPv4 socket: Cannot assign requested address
2013-06-18 10:08:58 CEST HINT:  Is another postmaster already running on port 5432? If not, wait a few seconds and retry.
2013-06-18 10:08:58 CEST WARNING:  could not create listen socket for "172.16.34.24"
2013-06-18 10:08:58 CEST FATAL:  could not create any TCP/IP sockets
[/INDENT]

When trying to upgrade, this error destroys my day:
I run the command ->  sudo apt-get upgrade
but, nothing happens - due to above failure.

Why is this problem occuring now and what can I do to fix it / bypass it ?

Regards, G

---

### Post by SeijiSensei on 2013-06-18
Use "ps ax | grep postmaster" to see if there is another instance already running.  If so, note its process ID, the first entry in the line returned, then run "sudo kill -9 PID" replacing PID with the appropriate process ID.  Here, for instance, is the entry corresponding to PostgreSQL on my server:

```
10186 ?        S     14:37 /usr/bin/postmaster -p 5432 -D /var/lib/pgsql/data
```

so I would issue a "sudo kill -9 10186" to stop it.

First, though, have you tried shutting it down cleanly with the "sudo service postgresql stop" command?

---

### Post by Gudjon on 2013-06-19
Hello S!

Thank you for your effort.
No process running : ps ax | grep postmaster

Still stuck.

Regards, G

---

### Post by SeijiSensei on 2013-06-19
First, are you sure the machine has address 172.16.34.24?  What does ifconfig say?

Are you using a firewall?  Is it blocking port 5432 on 172.16.34.24?  I've found that services may not bind to an interface/port that is globally blocked by iptables.  

If you run "telnet 172.16.34.24 5432" from the machine itself what happens?  Do you get a response?

Have you tried rebooting?

---

### Post by Gudjon on 2013-06-19
Hi!

The address is wrong
2013-06-19 17:14:38 CEST WARNING:  could not create listen socket for "172.16.34.24"

>ifconfig 
 inet addr:192.168.10.163  Bcast:192.168.10.255  Mask:255.255.255.0

So I have the 192.168.10.163

I had the wrong settings in my /etc/hosts file
Now I edited that : so the only one left is:
127.0.0.1    localhost

I restarted the computer.
The same fault is left.

hmmm.

regards, G

---

### Post by SeijiSensei on 2013-06-19
What address is specified as the "listen" address in postgresql.conf?  By default it will only bind to localhost.  My copy reads:

```

listen_addresses = 'localhost'     # what IP address(es) to listen on;
                    # comma-separated list of addresses;
                    # defaults to 'localhost', '*' = all

```
 If you want to bind to all addresses, you need to use "listen_addresses=*".  You'll also probably have to adjust the settings in pg_hba.conf as well.

---

### Post by Gudjon on 2013-06-20
Hello Sensje :)

My file says :
listen_addresses = '172.16.34.24'               # what IP address(es) to listen on;

Changed it to 'localhost' and it seems to solve my problem!!

Thanks so much.
This is due to my lack of knowledge regarding postgresql, I am 
trying / still just thinking / to switch from mysql to postgresql ...
So this is definitely a move in the right direction.

Thanks!!

-G

---

