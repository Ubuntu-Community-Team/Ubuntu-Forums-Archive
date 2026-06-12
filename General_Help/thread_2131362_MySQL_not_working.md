---
title: "MySQL not working"
date: 2013-04-01
forum: General Help
---

### Post by TheLG on 2013-04-01
Hello, I am now on this forum and I need help with my MySQL Server which is on my VPS with Ubuntu 12.10 Server.

Everything was fine 'till today, when I tried to login to PhpMyAdmin (as root) and I got theese two errors:


```
[SIZE=2][B][FONT=arial]#2002 Cannot log in to the MySQL server
[/FONT][/B][/SIZE]**[SIZE=2][B][FONT=arial]Connection for controluser as defined in your configuration failed[/FONT]**[/SIZE][/B]
```


So I googled for the solution, found something and commented theese lines in phpmyadmin config: 

```
**$cfg['Servers']['$i']['controluser'] **and **$cfg['Servers']['$']['controlpass']**
```

Now the error I was getting changed to 

```
[SIZE=3][B][FONT=arial][SIZE=2]#2003 Cannot log in to the MySQL server[/SIZE]

[/FONT][/B][/SIZE]
```[SIZE=3][FONT=arial][SIZE=3][SIZE=2]So I tried to[SIZE=2] access mysql [SIZE=2]from my VNC Client[SIZE=2], I log[SIZE=2]ged [SIZE=2]in as roo[SIZE=2]t and typed

```
**[SIZE=2][SIZE=2]$ mysql[/SIZE][/SIZE]**
```[/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/FONT][/SIZE][SIZE=3][B][FONT=arial]

[/FONT][/B][FONT=arial][SIZE=2]and I got this error:

[/SIZE][/FONT][/SIZE]```
**Can't connect to local MySQL server through socket '/var/lib/mysql/mysql.sock' (2)**
```[SIZE=3][FONT=arial][SIZE=2]

[SIZE=2]I checked and I cou[SIZE=2]ldn't find that file[SIZE=2]!
I tried creating it with *[SIZE=2]touch[/SIZE]*[SIZE=2], but didn't work..

Then I tried to start/restart [SIZE=2]mysql service but when I type *service my[SIZE=2]sql stop/start/restart [/SIZE]*[SIZE=2]I get:

```
**Job failed to start!**
```

I [SIZE=2]also tried **reinstall**[SIZE=2]**ing **mysql, php and apache2 and nothing [SIZE=2]worked!!
Please help me, my MC servers can't work wit[SIZE=2]hout MySQL!

[/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/FONT][/SIZE][SIZE=2]P[SIZE=2].S.
Today I[SIZE=2] changed ServerName in apache config because I was getting an[SIZE=2] [SIZE=2]error [SIZE=2]when I typed *service apache restart*:
[/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE]
```
**Could not reliably determine the server’s fully qualified domain name, using 127.0.1.1 for ServerName**
```

I'm not sure does that have anything to do with my MySQL problem.

And there is one little thing I did in sudoers (by typing *visudo*):
I wanted to execute commands from php as root so I added this line at the end of the file:

```
**www-data ALL=NOPASSWD: ALL**
```

Unfortunately, it didn't work so I removed that line..

Please help A.S.A.P.!

Thank you very much,
Leon Grdic

---

### Post by d4m1r on 2013-04-01
Is it a paid VPS? In that case, you should have the option to basically nuke it and start over if even a reinstall hasn't helped...SolusVM control panel comes to mind.

---

### Post by jonobr on 2013-04-01
Hello



try and find the sock file using

sudo find / -name *.sock

check your my.cnf file and ensure that matches whats in there

my.cnf should be in /etc/mysql

e.g 

# Remember to edit /etc/mysql/debian.cnf when changing the socket location.
[client]
port            = 3306
socket          = /var/run/mysqld/mysqld.sock

---

### Post by TheLG on 2013-04-02
> **d4m1r said:**
> Is it a paid VPS? In that case, you should have the option to basically nuke it and start over if even a reinstall hasn't helped...SolusVM control panel comes to mind.

Yes, it's paid host, but if I reinstall I would loose all databases!

---

### Post by Wim Sturkenboom on 2013-04-02
> **TheLG said:**
> 
```

Can't connect to local MySQL server through socket '/var/lib/mysql/mysql.sock' (2)

```

indicates that the server is not started. So you will not be able to connect anyway. Check the mysql error logs to find pointers as to why the service does not start.

---

### Post by TheLG on 2013-04-02
> **jonobr said:**
> Hello



try and find the sock file using

sudo find / -name *.sock

check your my.cnf file and ensure that matches whats in there

my.cnf should be in /etc/mysql

e.g 

# Remember to edit /etc/mysql/debian.cnf when changing the socket location.
[client]
port            = 3306
socket          = /var/run/mysqld/mysqld.sock

Thank you very much for your reply!
After typing sudo find / -name *.sock i got only /run/proftpd.sock!
Nothing else was found..

---

### Post by TheLG on 2013-04-02
> **Wim Sturkenboom said:**
> indicates that the server is not started. So you will not be able to connect anyway. Check the mysql error logs to find pointers as to why the service does not start.


But where can I find logs?
And I think that there is no reason for checking logs because mysql socket is missing!

---

### Post by Wim Sturkenboom on 2013-04-02
No, the socket file is created by the mysql daemon when the mysql deamon is started. If it fails to start (or when you stop the service), the socket file is removed again.

The log can be found in the directory /var/log/mysql (if you have a standard setup)

---

### Post by TheLG on 2013-04-02
> **Wim Sturkenboom said:**
> No, the socket file is created by the mysql daemon when the mysql deamon is started. If it fails to start (or when you stop the service), the socket file is removed again.

The log can be found in the directory /var/log/mysql (if you have a standard setup)

Thank you for your reply, I opened error.log located in that folder but it's empty.. There are also some files named error.log.1.gz but when I open it with nano it's empty...
Also, mysql on my server does not create a socket..

Thank you..

---

### Post by btindie on 2013-04-02
Type the following to see if it's actually running ```
ps -p $(pgrep -x mysqld) -f
```

You can check the status of the daemon with ```
sudo service mysql status
```

If it's appears to not be running then try starting it manually with ```
sudo service mysql start
``` it should provide output indicating if it started OK or not.

You can run the first two commands again to confirm it's running and also ```
ls -l /var/run/mysqld/mysqld.sock
``` to check that it's created the UNIX domain socket.

---

### Post by TheLG on 2013-04-02
> **btindie said:**
> Type the following to see if it's actually running ```
ps -p $(pgrep -x mysqld) -f
```

You can check the status of the daemon with ```
sudo service mysql status
```

If it's appears to not be running then try starting it manually with ```
sudo service mysql start
``` it should provide output indicating if it started OK or not.

You can run the first two commands again to confirm it's running and also ```
ls -l /var/run/mysqld/mysqld.sock
``` to check that it's created the UNIX domain socket.

Thanks but when I type
 ps -p $(pgrep -x mysqld) -f
I get Process ID list syntax error..
By typing
 sudo service mysql status
I get mysql stop/waiting
And when I typed
 ls -l /var/run/mysqld/mysqld.sock
I got No such file or directory..

---

### Post by TheLG on 2013-04-03
*BUMP*!!!
Can you please help me?
I think that I am going to reinstall my VPS but for that I need to backup my databases, can you tell me where are they located?

---

### Post by SeijiSensei on 2013-04-03
They are in /var/lib/mysql.  I recovered a server for a client in the same situation.  First, back up this directory.  Next, on the new server install mysql, and back up the /var/lib/mysql directory it creates just for good measure.  Now stop the new mysql server with "sudo service mysql stop", move /var/lib/mysql to /var/lib/mysql.bak, then copy over the old directory, and restart mysql with "sudo service mysql start".  That worked for me.

You should learn how to use mysqldump to create backups of your database.  I make a backup every day and copy it to a remote location over the Internet for safe keeping.  You'll need to write a little script that you can run with cron.  [I posted one here]("http://ubuntuforums.org/showthread.php?t=1580676&p=9882114&viewfull=1#post9882114"); you're welcome to give it a try.

---

### Post by TheLG on 2013-04-03
Thank you very much for your reply.
I am going to reinstall my VPS..
But there is just one little problem, i don't have backup space, so can anybody who has 1 GB of backup space contact me in pm so i can backup my data for few hours!
Thanks!

---

### Post by SeijiSensei on 2013-04-03
Can you not copy it over the Internet with something like scp or rsync?

When I have moved things between virtual hosts, I obtain the new host first, then copy things over the Internet between the old and new virtual machines.  Don't bother reformatting this machine, just set up a new one and delete the old one when you are finished.  It's a lot easier and a lot safer, too.

---

### Post by TheLG on 2013-04-03
I would do that but by host does not want to give me two VMs.. Because of that I am searching for a nice person who would like to borrow me FTP account with 1GB space so I can backup my data..

---

### Post by Cheesemill on 2013-04-03
Just back it up onto your own machine, and restore it when your done.

Do you not have 1G of space free on whatever machine you are using?

---

### Post by TheLG on 2013-04-03
Hou don't understand..
I have 800 GB but if I reinstall from my panel I will loose all data!!

---

### Post by Cheesemill on 2013-04-03
> **TheLG said:**
> Hou don't understand..
I have 800 GB but if I reinstall from my panel I will loose all data!!

You said you were after 1GB of backup space.

Just use your home computer to backup on to.

---

### Post by TheLG on 2013-04-03
Ufg, I just looked at my backup archive and it sizes 2 GB..
On my VPS I have about 800 GB free space, and if I reinstall it I will loose everything, all files..
There is an option from my hosting provider so I can buy an extra backup space but it's really very very expensive! On my PC i have very slow connection and if I try to download 2 GB file and after reinstallation upload it, that may take ages! So I am asking here if anybody here has own Server/PC with FTP and fast connection so I can backup my data there just for few hours!
Thanks again!

---

### Post by jonobr on 2013-04-04
>  Server/PC with FTP and fast connection so I can backup my data there just for few hours!

Kidding right?

---

### Post by TheLG on 2013-04-04
> **jonobr said:**
> Kidding right?

I wasn't kidding..
But thanks anyway, I found free FTP Servers..

---

