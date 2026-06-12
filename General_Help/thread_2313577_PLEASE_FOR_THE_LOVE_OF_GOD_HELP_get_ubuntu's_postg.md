---
title: "PLEASE FOR THE LOVE OF GOD HELP get ubuntu's postgresql to listen for external"
date: 2016-02-13
forum: General Help
---

### Post by JoGotta on 2016-02-13
I have changed the listening value in the postgres config file to '*' and I have even tried just entering only my IP address there but nothing I do seems to get postgresql to listen on my IP address and not on local host

Starting Nmap 6.40 ( [http://nmap.org](http://nmap.org) ) at 2016-02-13 16:44 ESTNmap scan report for jogotta-70A4000HUX.fios-router.home (192.168.1.156)
Host is up (0.00024s latency).
Not shown: 998 closed ports
PORT     STATE SERVICE
80/tcp   open  http
8009/tcp open  ajp13
 Starting Nmap 6.40 ( [http://nmap.org](http://nmap.org) ) at 2016-02-13 16:42 EST
Nmap scan report for localhost (127.0.0.1)
Host is up (0.00024s latency).
Not shown: 996 closed ports
PORT     STATE SERVICE
80/tcp   open  http
631/tcp  open  ipp
5432/tcp open  postgresql
8009/tcp open  ajp13

---

### Post by CharlesA on 2016-02-13
Check your postgres config.

[http://www.cyberciti.biz/tips/postgres-allow-remote-access-tcp-connection.html](http://www.cyberciti.biz/tips/postgres-allow-remote-access-tcp-connection.html)

Most databases only listen on localhost by default and need to be changed if you are going to be using them from remote machines.

---

### Post by JoGotta on 2016-02-13
I have already been living on that website for two days now.  The start up as a service I think is causing it to ignore the config files

---

### Post by CharlesA on 2016-02-13
What about here?
[http://askubuntu.com/questions/423165/remotely-access-postgresql-database](http://askubuntu.com/questions/423165/remotely-access-postgresql-database)
[https://help.ubuntu.com/community/PostgreSQL](https://help.ubuntu.com/community/PostgreSQL)

---

### Post by JoGotta on 2016-02-13
#listen_addresses = '192.168.1.156'		# what IP address(es) to listen on;					# comma-separated list of addresses;
					# defaults to 'localhost'; use '*' for all
					# (change requires restart)
port = 5432				# (change requires restart)

See?  I have restarted the service.. and done a force reload.. I checked the log files for errors... this is the liste.. oh **** it's commented out

---

### Post by CharlesA on 2016-02-13
listen_addresses is commented out. Remove the # from in front and restart the service.

---

