---
title: "MythBackend authentication problem"
date: 2005-09-12
forum: General Help
---

### Post by igb on 2005-09-12
I am in the process of setting up MythTV. I have got MySQL installed and running. The mythconverg database and associated tables are created. I have got a mythtv user in MySQL and set the password to mythtv. 

My /etc/mythtv/sql.txt file looks like this:

DBHostName=localhost
DBUserName=mythtv
DBName=mythconverg
DBPassword=mythtv

For the moment I have disabled the mythtv-backend daemon and am trying to start it manually. When I run mythbackend either as root or the mythtv user I get the following error:

Session management error: Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed
2005-09-11 15:27:26.535 New DB connection, total: 1
Starting up as the master server.
2005-09-11 15:27:26.594 New DB connection, total: 2
2005-09-11 15:27:26.681 DVB#0 DVB SI Table Parser Started
2005-09-11 15:27:26.681 DVB#0 ERROR - Opening DVB frontend device failed.
          (2) No such file or directory
2005-09-11 15:27:26.771 New DB scheduler connection
2005-09-11 15:27:26.820 mythbackend version: 0.18.1.20050510-1 [www.mythtv.org](www.mythtv.org)
2005-09-11 15:27:26.820 Enabled verbose msgs : important general
QServerSocket: failed to bind or listen to the socket
Failed to bind to port 6543

If I log in as mythtv at a terminal I can log into MySQL OK:

mysql -u mythtv -pmythtv mythconverg

For some reason mythbackend deosn't want to talk my the MySQL server. Any suggestions as to what's going on?

Ian.

---

### Post by debenham on 2005-09-13
Check what is in /home/mythtv/.mythtv/mysql.txt and /root/.mythtv/mysql.txt
Mythtv sometimes checks them for sql login details

---

### Post by igb on 2005-09-13
Thanks. I had already tried that :mad: Eventually, I uninstalled the packages, nuked the mythtv user/group and all MythTV files, then re-installed. That seems to have fixed the problem.

Ian.

---

