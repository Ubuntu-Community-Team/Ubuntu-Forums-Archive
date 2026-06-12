---
title: "MySQL Error 2003 - Can't connect MySQL on'IP Address'"
date: 2008-02-04
forum: General Help
---

### Post by sbrennan on 2008-02-04
Hello,

This is driving me crazy. I just setup a new installation of Ubuntu 6.06 Server which has MySQL 5.0.22, and moved over all MySQL tables from a previous installation (except for 'information_schema' and 'mysql' tables) and setup appropriate permissions, from what I can tell:

CREATE USER 'user'@'localhost' IDENTIFIED BY 'password';
GRANT ALL PRIVILEGES ON database.* TO 'user'@'localhost' IDENTIFIED BY 'password';

CREATE USER 'user'@'%' IDENTIFIED BY 'password';
GRANT ALL PRIVILEGES ON database.* TO 'user'@'%' IDENTIFIED BY 'password';

However, I can't connect, either through another box that uses the same database for its webpages or through GUI administrator toolkits from Windows XP, which keeps giving me the error in the subject of my post. However, Apache pulls data from mysql (using the user@localhost account) just fine when serving pages from this machine.

I can of course SSH and HTTP into the machine just fine as well and connect with this user through localhost from command line. Anyone know what's up? There are no firewalls in the equation, either.

---

### Post by faulkes on 2008-02-04
> **sbrennan said:**
> Hello,

CREATE USER 'user'@'%' IDENTIFIED BY 'password';
GRANT ALL PRIVILEGES ON database.* TO 'user'@'%' IDENTIFIED BY 'password';



Looks like the second GRANT command has a syntax error in it, if that was a paste, it should be
**_`user`@`%`_**

Faulkes

---

### Post by sbrennan on 2008-02-04
It wasn't a paste, but I tried switching the single quotes to ` just in case, but there was no difference. Still can't connect :(

I also checked my.conf and bind-address is commented out, as well.

---

### Post by faulkes on 2008-02-04
Have you also issued a:

```

FLUSH PRIVILEGES;

```

command?

Faulkes

---

### Post by sbrennan on 2008-02-04
Sorry, yes, I've tried that too...

The only thing I can think of is that I have a problem setup with my networking. When I installed the system, I had a different hostname and static IP address until I was happy with things, and then I switched out the hostname and IP address with a different, older machine I am retiring.

However, I've updated /etc/hosts, /etc/hostname, and /etc/networking/interfaces. I've restarted networking and rebooted a few times as well. Maybe I am missing something?

---

### Post by faulkes on 2008-02-04
I would start having a look at what is actually in the mysql database (iirc it's called Users) to see if there is anything off.

Aside from that, the only thing I can think of doing is turning on some extra debug to see what is happening with the connection, heck, even telnet to port 3306 and see what it spits out at you.

Faulkes

---

### Post by sbrennan on 2008-02-04
I really appreciate your help! Ummm...can you tell me how to telnet to port 3306? I've never messed with telnet too much :)

I've been running queries against the users table and everything looks ok.

---

### Post by damir_1105 on 2008-02-04
check config file of mysql. can be that is localhost only allowed to access database from 127.0.0.1

---

### Post by sbrennan on 2008-02-04
Figured it out:

telnet [ip address] 3306

it's saying connection refused. Hmm....

---

### Post by sbrennan on 2008-02-04
> **damir_1105 said:**
> check config file of mysql. can be that is localhost only allowed to access database from 127.0.0.1

I feel stupid! Thanks!

I swore I had the  'bind-address' line in my.cnf commented out but that must have been one of the other three boxes  I have open in Putty :/

Thanks....:KS

---

### Post by damir_1105 on 2008-02-04
check   ```
/etc/mysql/my.cnf
```
by default it bind to 127.0.0.1

---

### Post by sbrennan on 2008-02-04
> **damir_1105 said:**
> check   ```
/etc/mysql/my.cnf
```
by default it bind to 127.0.0.1


Thank you, Damir, I'm all fixed :)

---

### Post by vanderkerkoff on 2008-02-05
Hello there.

I've just followed this solution to allow our main sql backup machine to go and grab a number of databases on a new machine and back them up.

I've granted all privileges to a specific username on a specific IP address, I'm not using %, which I think is a wildcard character?

I've now commented out the bind address, which in effect opens the database up to connections from anywhere.

Could I set the bind address to be the IP address of the mysql backup server and not have any problems with the mysql running on the machine itself?  

That sounds more secure to me.

Your example seems to say to me that you've now opened up the dbase to any ip address by using % and also uncommenting the bind address.

Please let me know if I'm reading this incorreclty.

---

### Post by damir_1105 on 2008-02-05
ie. one of your database host's ip binding is 10.10.10.66/255.255.0.0

this will list the server to respond only to hosts in the 10.10.x.x
range, all other (including localhost!!) will be refused.

bind-address=10.10.10.66/255.255.0.0

try configurnig iptables that accept just your backup server connections to mysql port.

---

