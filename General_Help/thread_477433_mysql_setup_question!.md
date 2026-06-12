---
title: "mysql setup question!"
date: 2007-06-18
forum: General Help
---

### Post by dysolve on 2007-06-18
I am doing the following as per a tutoral i found,
"mysqladmin -h root@server1 -u root -p password"

then i am asked
"Enter password:" 

but i get the following error

"mysqladmin: connect to server at 'root@server1' failed
error: 'Unknown MySQL server host 'root@server1' (1)'
Check that mysqld is running on root@server1 and that the port is 3306.
You can check this by doing 'telnet root@server1 3306'"

when i check  to see if it running i get this:

"telnet: could not resolve root@server1/3306: Name or service not known"

any idea whats going on? what am i doing wrong?
thanks
David

---

### Post by upbeat.linux on 2007-06-18
What are you trying to accomplish?  Did you setup MySQL on the remote server?

1. if you're not sure how its setup you should contact the admin for that server, otherwise, by default, MySQL is set to deny remote requests from the root account.

2. check out the man pages for mysqladmin they will be a lot more helpful than a tutorial as it will give you a great explanation of what mysqladmin can do. Launch a prompt and enter "man mysqladmin" or just google "man mysqladmin.

3. a better way to test if port 3306 is open is to do one of the following

telnet server1 3306

or 

nmap -sT server1

The first should return the mysql version and some garbledy gook and the second will return a list of open ports on that server.

---

