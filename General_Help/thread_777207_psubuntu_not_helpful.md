---
title: "psubuntu not helpful"
date: 2008-05-01
forum: General Help
---

### Post by hart02 on 2008-05-01
I posted this originally at psubuntu

> **I have been trying install mythtv on my ps3**. i have bought a **Plextor ConvertX PVR PX-TV402U** and i have a 250 gig hdd. what i want is to have the ps3 as the frontend, the backend the Plextor ConvertX PVR PX-TV402U and the master backend a directory on my Lacie EDmini. However, i have not had such great luck with the setup. so i went to my log and
posted this:
QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2008-04-20 15:41:21.161 Using runtime prefix = /usr, libdir = /usr/lib
2008-04-20 15:41:21.370 Empty LocalHostName.
2008-04-20 15:41:21.481 Using localhost value of Bmans PS3
2008-04-20 15:41:22.022 New DB connection, total: 1
2008-04-20 15:52:03.321 Using runtime prefix = /usr, libdir = /usr/lib
2008-04-20 15:52:03.597 Empty LocalHostName.
2008-04-20 15:52:03.605 Using localhost value of Bmans PS3
2008-04-20 15:52:04.668 New DB connection, total: 1
2008-04-20 15:55:14.574 Unable to connect to database!
2008-04-20 15:55:14.603 **Driver error was [1/2003]**:
QMYSQL3: Unable to connect
Database error was:
**Can't connect to MySQL server on** '192.168.1.135' (110)

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2008-04-20 15:58:24.547 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError? Strange...
...............................................................
2008-04-20 15:58:27.105 UPnPautoconf() - No UPnP backends found
2008-04-20 15:58:27.106 No UPnP backends found

**No UPnP backends found**

Would you like to configure the database connection now? [yes] 
[console is not interactive, using default 'yes']
Database host name: [192.168.1.135] 
[console is not interactive, using default '192.168.1.135']
Should I test connectivity to this host using the ping command? [yes] 
[console is not interactive, using default 'yes']
Database non-default port: [0] 
[console is not interactive, using default '0']
Database name: [mythconverg] 
[console is not interactive, using default 'mythconverg']
Database user name: [mythtv] 
[console is not interactive, using default 'mythtv']
Database password: [lemons] 
[console is not interactive, using default 'lemons']
Unique identifier for this machine (if empty, the local host name will be used): 
[console is not interactive, using default '']
Would you like to use Wake-On-LAN to retry database connections? [no] 
[console is not interactive, using default 'no']
2008-04-20 16:01:36.170 Unable to connect to database!
2008-04-20 16:01:36.174 Driver error was [1/2003]:
QMYSQL3: Unable to connect
Database error was:
Can't connect to MySQL server on '192.168.1.135' (110)
If more info is required let me know.

after that i posted this to answer questions they had

> well i'm sorry for double posting but i end up waiting too long for a response. yes i have the lastest version of mythtv. yes i have done this:
Setup mysql database mythconverg

Set the root password for the mysql database. (replace mysqlpassword with your own) 

Open a Terminal window 
> mysql -u root password mysqlpassword

Setup the initial database. Note - the mc.sql file should have been installed along with the mythtv documentation onto your system. The default location for this file is shown below, however it may have been relocated elsewhere according to your distribution's documentation rules, so you may have to use a search (find, locate, etc) tool to reveal its whereabouts. (The following command will prompt for password) 
> mysql -u root -p < /usr/share/mythtv/sql/mc.sql

How to Reset the Root Password (Slackware): 

Login as a root 
> su -

Stop the database 
> /etc/rc.d/rc.mysqld stop

Set the initial file for a new root database password 
> echo "SET PASSWORD FOR 'root'@'localhost' = PASSWORD('new_password');" > /var/lib/mysql/mysql-init

Change the user and group ownership 
> chown mysql.mysql /var/lib/mysql/mysql-init

Start a database manually 
> /usr/bin/mysqld_safe --init-file=/var/lib/mysql/mysql-init &

Login to the database as a root with a new password 
> mysql -u root -p new_password
**and i edited /etc/mythtv/mysql.txt.**
the backend is running and it still cannot connect to the database.
i still get this: 2008-04-20 15:41:21.161 Using runtime prefix = /usr, libdir = /usr/lib
2008-04-20 15:41:21.370 Empty LocalHostName.
2008-04-20 15:41:21.481 Using localhost value of Bmans PS3
2008-04-20 15:41:22.022 New DB connection, total: 1
2008-04-20 15:52:03.321 Using runtime prefix = /usr, libdir = /usr/lib
2008-04-20 15:52:03.597 Empty LocalHostName.
2008-04-20 15:52:03.605 Using localhost value of Bmans PS3
2008-04-20 15:52:04.668 New DB connection, total: 1
2008-04-20 15:55:14.574 Unable to connect to database!
2008-04-20 15:55:14.603 Driver error was [1/2003]:
QMYSQL3: Unable to connect
Database error was:Can't connect to MySQL server on '192.168.1.135' (110) only i changed it to 192.168.1.148. 
there is also a host authentication failure message.
**Never have i been so frustated by the lack of support and lack of users in the forums. if linux is to succeed, then users should try posting in one centralized location [http://www.thelinuxvault.net/wiki/Main_Page.they](http://www.thelinuxvault.net/wiki/Main_Page.they) should know that not everyone is smart and/or intelligent enough to use linux. I am not one of those people, but that does not mean I don't struggle with things.I can understand that double posting clogs forums, but old threads don't often get answered.There should be a unified notifier of already posted threads or a search engine where you type a question, a description and its topic with advance feature to reduce forum clutter and to help more people faster.** So would it hurt you to check more often to prevent forum clutter? I will try to not double post.Seriously though what is being done is ridiculous. so I still have no answers. So i posted this at the LAS forum:> **I only have a standard tv.i cannot use ydl.** so does anyone know a solution to the problem i posted here? [http://psubuntu.com/forums/viewtopic.php?f=12&t=109]("http://psubuntu.com/forums/viewtopic.php?f=12&t=109")
[http://psubuntu.com/forums/viewtopic.php?f=12&t=132]("http://psubuntu.com/forums/viewtopic.php?f=12&t=132")
also i get this:**Tried to connect to session manager, Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed**and I get nothing. Now I am angered for not only for this psubuntu but also for Ubuntu dropping PPC support:mad::confused:, but i don't hate Ubuntu and i can forgive you if you can at least give more PS3 Support.You could perhaps make an official Psubuntu OS with things from Mythtv to Bluetooth and wifi support as well as give a choice of different gui  environments at install like gnome, fluxbox etc. That would make my day:KS.

---

### Post by Monicker on 2008-05-01
I have been using Mythtv for a couple of years now.  Something looks wrong with those instructions.  The default database user for the mythconverg mysql database is "mythtv".  That is the account which you need to make sure has the proper password.  Changing the root mysql user password will not help.

Verify the user in ~/.mythtv/mysql.txt, and verify that account has permissions in mysql.  Are you using a separate mythtv frontend and backend, or are they both running on the same machine?

---

### Post by hart02 on 2008-05-01
they are on the same machine.

---

### Post by hart02 on 2008-05-01
> **Monicker said:**
> I have been using Mythtv for a couple of years now.  Something looks wrong with those instructions.  The default database user for the mythconverg mysql database is "mythtv".  That is the account which you need to make sure has the proper password.  Changing the root mysql user password will not help.

Verify the user in ~/.mythtv/mysql.txt, and verify that account has permissions in mysql.  Are you using a separate mythtv frontend and backend, or are they both running on the same machine?

how do i verify that my mythtv account has permissions in mysql?

---

### Post by skymera on 2008-05-01
Which version of Ubuntu are you on?

8.04 is reported to not work very well.
7.10 is to work pretty well.

---

### Post by Monicker on 2008-05-01
> **hart02 said:**
> how do i verify that my mythtv account has permissions in mysql?

From a terminal session log into mysql using the username and password contained ~/.mythtv/mysql.txt

Here is what I see on my system:

```
mysql -u mythtv -p

<enter password>


mysql> show grants for 'mythtv'@'localhost';
+---------------------------------------------------------------------------------------------------------------+
| Grants for mythtv@localhost                                                                                   |
+---------------------------------------------------------------------------------------------------------------+
| GRANT USAGE ON *.* TO 'mythtv'@'localhost' IDENTIFIED BY PASSWORD '*XXXXX' |
| GRANT ALL PRIVILEGES ON `mythconverg`.* TO 'mythtv'@'localhost'                                               |
+---------------------------------------------------------------------------------------------------------------+
2 rows in set (0.01 sec)
```

As you can see, the mythtv user has all privileges on the mythconverg database, which is where mythtv stores all of its recording and configuration details.

---

### Post by Monicker on 2008-05-01
I just realized something else which could be an issue.  Verify that you have configured the proper ip address for mysql in the backend configuration.  Check /etc/mysql/my.cnf and look at the bind-address line; that ip address should match what you specified in your mythtv configuration.

---

### Post by hart02 on 2008-05-01
> **skymera said:**
> Which version of Ubuntu are you on?

8.04 is reported to not work very well.
7.10 is to work pretty well.7.10 on a ps3

---

### Post by hart02 on 2008-05-02
so I entered your code
mysql -u mythtv -p which prompted me to enter my password.it gave me:ERROR 1045 (28000): Access denied for user 'mythtv'@'localhost' (using password: YES)
.then i tried this:
mysql -u mythtv -p password xxxxxx

all in the same line. It gave me a long output message about mysql which i dont know all what it said.
I did not get this output:

mysql> show grants for 'mythtv'@'localhost';
| Grants for mythtv@localhost
| GRANT USAGE ON *.* TO 'mythtv'@'localhost' IDENTIFIED BY PASSWORD '*XXXXX' |
| GRANT ALL PRIVILEGES ON `mythconverg`.* TO 'mythtv'@'localhost'
2 rows in set (0.01 sec)

I am not whether I should i should enter the code as root or as my user.

I don't know what this thing at the beginning means:~/

I believe the path to mythconverg is /usr/share/mythtv/sql/mc.sql
or it could be var.

I checked /etc/mysql/my.cnf. Its bind-address IP line is
192.168.1.148.

where is the the mythtv backend config file stored at?

is any more info needed?

---

### Post by hart02 on 2008-05-02
i also edited the mythtv accounts password at the root terminal to see if could login as a user

---

### Post by Monicker on 2008-05-02
~/ is just a shorthand way of specifying your home directory: ~/.mythtv is the same as /home/username/.mythtv.

When you first entered "mysql -u mythtv -p" and entered a password which was not accepted, was it the same password which is in ~/.mythtv/mysql.txt?

The location of the database files themselves would be in /var/lib/mysql.  The mc.sql file is just telling mysql how to configure the database for use with mythtv, but it is not the actual database which mysql is using.

To verify your mythtv backend settings:
```

sudo /etc/init.d/mythbackend stop
mythtv-setup
```

There may already be an icon for the mythtv-setup in your Applications menu.

As it stands now, you do not appear to be using the proper password for the mythtv user account which connects to the mysql database.  You also appear to have specified the wrong ip address for the mysql database in the mythtv configuration, which is causing the "Can't connect to MySQL server on '192.168.1.135' (110)'" error messages, since your mysql configuration shows that it is listening for connections to ip address 192.168.1.148.  Which one is the actual ip address of the machine which is running mythtv?

---

### Post by hart02 on 2008-05-03
the ip for the machine mythtv is on is 192.168.1.148

---

### Post by hart02 on 2008-05-04
I think i have screwed up the MYSQL settings to get  ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)instead of ERROR 1045 (28000): Access denied for user 'mythtv'@'localhost' (using password: YES) Is there a way to redo the whole thing like start over?

---

### Post by hart02 on 2008-05-04
I changed the password in /home/username/.mythtv/mysql.txt.

---

### Post by Zorael on 2008-05-04
> **hart02 said:**
> I posted this originally at psubuntu

...
> Never have i been so frustated by the lack of support and lack of users in the forums. if linux is to succeed, then users should try posting in one centralized location [http://www.thelinuxvault.net/wiki/Main_Page.they](http://www.thelinuxvault.net/wiki/Main_Page.they) should know that not everyone is smart and/or intelligent enough to use linux. I am not one of those people, but that does not mean I don't struggle with things.I can understand that double posting clogs forums, but old threads don't often get answered.There should be a unified notifier of already posted threads or a search engine where you type a question, a description and its topic with advance feature to reduce forum clutter and to help more people faster. So would it hurt you to check more often to prevent forum clutter? I will try to not double post.Seriously though what is being done is ridiculous.
 so I still have no answers. So i posted this at the LAS forum:

...

and I get nothing. Now I am angered for not only for this psubuntu but also for Ubuntu dropping PPC support:mad::confused:, but i don't hate Ubuntu and **i can forgive you if you can at least give more PS3 Support**.You could perhaps make an official Psubuntu OS with things from Mythtv to Bluetooth and wifi support as well as give a choice of different gui  environments at install like gnome, fluxbox etc. That would make my day:KS.
Huh. You can forgive us?

[SIZE="5"][Please read this, notably the **3a** section.](http://linux.oneandoneis2.org/LNW.htm)[/SIZE]

> **Problem 3a excerpt]Windows users are more or less in a customer-supplier relationship: They pay for software, for warranties, for support, and so on. They expect software to have a certain level of usability. They are therefore used to having rights with their software: They have paid for technical support and have every right to demand that they receive it. They are also used to dealing with entities rather than people: Their contracts are with a company, not with a person.

Linux users are in more of a community. They don't have to buy the software, they don't have to pay for technical support. They download software for free & use Instant Messaging and web-based forums to get help. They deal with people, not corporations.

A Windows user will not endear himself by bringing his habitual attitudes over to Linux, to put it mildly.

The biggest cause of friction tends to be in the online interactions: A "3a" user new to Linux asks for help with a problem he's having. When he doesn't get that help at what he considers an acceptable rate, he starts complaining and demanding more help. Because that's what he's used to doing with paid-for tech support. The problem is that this isn't paid-for support. This is a bunch of volunteers who are willing to help people with problems out of the goodness of their hearts. The new user has no right to demand anything from them, any more than somebody collecting for charity can demand larger donations from contributors.

In much the same way, a Windows user is used to using commercial software. Companies don't release software until it's reliable, functional, and user-friendly enough. So this is what a Windows user tends to expect from software: It starts at version 1.0. Linux software, however, tends to get released almost as soon as it's written: It starts at version 0.1. This way, people who really need the functionality can get it ASAP said:**
> If a "3a" user runs into trouble with Linux, he'll complain: The software hasn't met his standards, and he thinks he has a right to expect that standard. His mood won't be improved when he gets sarcastic replies like "I'd demand a refund if I were you"

So, to avoid problem #3a: _Simply remember that you haven't paid the developer who wrote the software or the people online who provide the tech support. They don't owe you anything._[/b]
Point in case:
```
**Tags**
anger, desire, disatisfaction, helpme, problems
```

[quote=Problem 7 excerpt]Linux is not interested in market share. Linux does not have customers. Linux does not have shareholders, or a responsibility to the bottom line. Linux was not created to make money. Linux does not have the goal of being the most popular and widespread OS on the planet.

All the Linux community wants is to create a really good, fully-featured, free operating system. If that results in Linux becoming a hugely popular OS, then that's great. If that results in Linux having the most intuitive, user-friendly interface ever created, then that's great. If that results in Linux becoming the basis of a multi-billion dollar industry, then that's great.

It's great, but it's not the point. The point is to make Linux the best OS that the community is capable of making. Not for other people: For itself. The oh-so-common threats of "Linux will never take over the desktop unless it does such-and-such" are simply irrelevant: The Linux community isn't trying to take over the desktop. They really don't care if it gets good enough to make it onto your desktop, so long as it stays good enough to remain on theirs. The highly-vocal MS-haters, pro-Linux zealots, and money-making FOSS purveyors might be loud, but they're still minorities.

That's what the Linux community wants: an OS that can be installed by whoever really wants it. So if you're considering switching to Linux, first ask yourself what you really want.

If you want an OS that doesn't chauffeur you around, but hands you the keys, puts you in the driver's seat, and expects you to know what to do: Get Linux. You'll have to devote some time to learning how to use it, but once you've done so, you'll have an OS that you can make sit up and dance.

If you really just want Windows without the malware and security issues: Read up on good security practices; install a good firewall, malware-detector, and anti-virus; replace IE with a more secure browser; and keep yourself up-to-date with security updates. There are people out there (myself included) who've used Windows since 3.1 days right through to XP without ever being infected with a virus or malware: you can do it too. Don't get Linux: It will fail miserably at being what you want it to be.

If you really want the security and performance of a Unix-based OS but with a customer-focussed attitude and an world-renowned interface: Buy an Apple Mac. OS X is great. But don't get Linux: It will not do what you want it to do.

It's not just about "Why should I want Linux?". It's also about "Why should Linux want me?"[/quote]
I don't have the expertise to help on this one issue, but even if I did, I wouldn't help you.

---

### Post by hart02 on 2008-05-04
Ok I might have gone over the edge with that segment.Still i like the idea of most distros using The Linux Vault wiki.

---

### Post by Monicker on 2008-05-04
> **hart02 said:**
> I think i have screwed up the MYSQL settings to get  ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)instead of ERROR 1045 (28000): Access denied for user 'mythtv'@'localhost' (using password: YES) Is there a way to redo the whole thing like start over?

Starting over is probably not necessary.  You can do that if you choose, but franky I don't think it will go any smoother than what it happening now.  What were you doing when you received that error message?  If you were attempting to connect from the machine which has the mysql database, then mysqld is probably not running.  What, if anything, did you change in mysql.cnf.


What happens when you do this?


```
sudo /etc/init.d/mysql restart
```


Does it fail to start back up?

---

### Post by hart02 on 2008-05-05
It runs now. but i still get get this:ERROR 1045 (28000): Access denied for user 'mythtv'@'localhost' (using password: YES) I thought that changing the mysql login password would fix the problem but that is  not the case.You said to check the backend configuration but i am not sure where that is stored.do you mean the mysql.txt file in the /home/user/.mythtv folder? > Check /etc/mysql/my.cnf and look at the bind-address line; that ip address should match what you specified in your mythtv configuration. i believe i changed that to 127.0.0.1. Unless I am absulotely know 
where my mythtv configuration is stored, fixing this will be hard.

---

### Post by hart02 on 2008-05-07
This is the output i got.

**cat /etc/issue**
Ubuntu 7.10 \n \l

You have new mail in /var/mail/brian

**dpkg -l|grep mythtv**
ii  mythtv                                     0.21.0-0ubuntu2~gutsy1               A personal video recorder application (clien
ii  mythtv-backend                             0.21.0-0ubuntu2~gutsy1               A personal video recorder application (serve
ii  mythtv-backend-master                      0.21.0-0ubuntu2~gutsy1               Metapackage to setup and configure a "Master
ii  mythtv-common                              0.21.0-0ubuntu2~gutsy1               A personal video recorder application (commo
ii  mythtv-database                            0.21.0-0ubuntu2~gutsy1               A personal video recorder application (datab
ii  mythtv-doc                                 0.21.0-0ubuntu2~gutsy1               A personal video recorder application (docum
ii  mythtv-frontend                            0.21.0-0ubuntu2~gutsy1               A personal video recorder application (clien
ii  mythtv-theme-mythcenter                    0.21.0-0ubuntu1~gutsy1               The MythCenter MythTV Theme
ii  mythtv-themes                              0.21.0-0ubuntu1~gutsy1               Additional themes metapackage for MythTV
ii  mythtv-transcode-utils                     0.21.0-0ubuntu2~gutsy1               Utilities used for transcoding MythTV tasks
ii  mythtvfs                                   0.5.0-1                              userspace filesystem client for MythTV
ii  ubuntu-mythtv-frontend                     0.21.0-0ubuntu2~gutsy1               Metapackage to setup and configure a "Fronte

**ifconfig**
Command 'ifconfig' is available in '/sbin/ifconfig'
The command could not be located because '/sbin' is not included in the PATH environment variable.
This is most likely caused by the lack of administrative priviledges associated with your user account.

Did this

**sudo ifconfig**
eth0      Link encap:Ethernet  HWaddr 00:19:C5:D4:EC:A6  
          inet addr:192.168.1.148  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::219:c5ff:fed4:eca6/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:605091 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1179862 errors:0 dropped:589561 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:44477710 (42.4 MB)  TX bytes:82655810 (78.8 MB)
          Interrupt:29 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:68 errors:0 dropped:0 overruns:0 frame:0
          TX packets:68 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:5276 (5.1 KB)  TX bytes:5276 (5.1 KB)

**grep bind-address /etc/mysql/my.cnf**
bind-address            = 192.168.1.148

**locate mythtv-setup**
/usr/share/app-install/desktop/mythtv-setup.desktop
/usr/share/applications/mythtv-setup.desktop.diverted
/usr/share/mythtv/mythtv-setup.sh
/usr/bin/mythtv-setup.real
/usr/bin/mythtv-setup

**mysql> select user,Host from user;**
+------------------+-----------+
| user             | Host      |
+------------------+-----------+
| root             | 127.0.0.1 | 
| root             | Bmans PS3 | 
| debian-sys-maint | localhost | 
| mythtv           | localhost | 
| root             | localhost | 
+------------------+-----------+
5 rows in set (0.07 sec)

mysql> 

hope this helps anyone

---

### Post by Monicker on 2008-05-07
Ok. Now in ~/.mythtv/mysql.txt, you should have something like the following:

```
DBHostName=192.168.1.148
DBUserName=mythtv
DBPassword=password
DBName=mythconverg
DBType=QMYSQL3
```

Am I correct?

---

### Post by hart02 on 2008-05-08
I believe it says

DBHostName=Bmans PS3
DBUserName=mythtv
DBPassword=password(gave it a new password)
DBName=mythconverg
DBType=QMYSQL3

The mythtv setup has Bmans PS3 as the hostname

If all I need to do is change the Host Name to an IP address, Then the problem is basically solved. I just need to verify this when i am able to.

---

### Post by hart02 on 2008-05-09
I got to it work.I gave mythtv mysql grant all permissions and logged in as it.now all i have to do is to:convert all my midi song to mp3 all at once & put them on my Lacie EDmini nas, configure mythgame to recognize the location of my roms,compile drivers for my Plextor ConvertX PVR PX-TV402U tv card, get an account at schedulesdirect.org,get mythmusic,mythphoto,and mythvideo to recognize the locations i specify, get mythstream to install,and specify another location for recordings. once i do that, I could setup other clients as well and i owe a lot to Monicker.Cheers:KS

---

### Post by johnniec on 2008-07-15
Hi,

I've spent some time trying to get the Plextor ConvertX TV tuner (PX-TV402U) to work with Ubuntu 7.10 on my ps3.

Until now I have only been able to compile and install the drivers.
The purpose is to use this with MythTv too.

Have you been able to use this TV card on the PS3 under Ubuntu?

If needed I can provide lots more info... 

Thanks,
John

---

