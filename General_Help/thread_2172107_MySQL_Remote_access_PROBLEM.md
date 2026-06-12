---
title: "MySQL Remote access PROBLEM"
date: 2013-09-03
forum: General Help
---

### Post by tamura2 on 2013-09-03
Hi,

I configured the MySQL on my Ubuntu server to access it remotely (I HAVE to access it remotely). Those basics configurations that we learn searching on the Google:

- I edited my.cnf and commented the [FONT=courier new]skip-external-licking [/FONT]and [FONT=courier new]bind-address: 127.0.0.1[/FONT] lines;

- The port used is 3306;

- I restarted the MySQL;

- I opened this port with the command: [FONT=courier new]sudo ufw allow 3306[/FONT] (i'm not using iptables because i don't know how to use it :confused:);

- I configured my modem (SagemCom Modem F@st 2764) to forward the 3306 port correctly;
PS: I configured my Apache and i can to access my PHPs pages normally, for this reason i think the problem is not the modem

- I tested the port using these sites that have this tool (one of them is [http://www.yougetsignal.com/tools/open-ports/](http://www.yougetsignal.com/tools/open-ports/)) and it returns that this port is open;

- So, i created a user for MySQL:
[FONT=courier new] CREATE USER 'user'@'localhost' IDENTIFIED BY 'my_pass';[/FONT]

- I granted the privileges to this user:
[FONT=courier new] GRANT ALL PRIVILEGES ON name_of_db.* TO 'user'@'%' IDENTIFIED BY 'my_pass';[/FONT]

- Locally (accessing the database with the local server IP) using the user created i access it successfully

- But, externally, using a MySQL client, i tried to access this database as the following:
Host: 185.98.658.2     Port: 3306
User: user
Pass: my_pass
Result: Can't connect to MySQL server on '185.98.658.2' (10061)

I did a simple PHP script to test it as the following:
Host: 185.98.658.2:3306
User: user     Pass: my_pass
Result: Can't connect to MySQL server on '185.98.658.2' (111)

I tried to access through a Android's app (Connect2SQL), and it returned:
failed to connect to /185.98.658.2(port 3306) after 100000ms: isConnected failed: ECONNREFUSED (Connection refused)

Well, i don't know more what can i do, somebody have any idea or suggestion? HELP ME! :cry:

Thanks a lot.

---

### Post by SeijiSensei on 2013-09-03
If the username is 'user'@'localhost' then that user can only connect over 127.0.0.1.  Try creating another username with 'user'@'%' and see if that works.  

I hate MySQL's whole authentication scheme with a passion.  I use PostgreSQL for many reasons, one of which is its approach to user and database management.

---

### Post by tamura2 on 2013-09-06
Thank you, it works!

---

