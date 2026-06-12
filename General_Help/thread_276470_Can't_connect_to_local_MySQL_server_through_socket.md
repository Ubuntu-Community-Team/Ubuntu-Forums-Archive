---
title: "Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)"
date: 2006-10-12
forum: General Help
---

### Post by johnusa on 2006-10-12
I am a LAMP newbie.
==== Environment ======
OS = Ubuntu 6.06
MySQL = v5.0.22
PHP = v5.1.6
Apache = v2.2.3
=======================
I started MySQL server with the command:
> mysqld_safe --user=mysql &
To verify that the database is running, I issued the command:
> mysqladmin version
I received the error:
> error: 'Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)'
Check that mysqld is running and that the socket: '/var/run/mysqld/mysqld.sock' exists!
Approximately 1 and 1/2 minutes later, I received the message:
> STOPPING server from pid file /var/run/mysqld/mysqld.pid
mysqld_safe[25877]: ended
I could not locate a file named "mysqld.sock" on my system.
Here is the test from my terminal session:
> root@johni-desktop:/usr/bin# mysqld_safe --user mysql &
[1] 25735
root@johni-desktop:/usr/bin# Starting mysqld daemon with databases from /var/lib/mysql
mysqld_safe[25799]: started

root@johni-desktop:/usr/bin# mysqladmin version
mysqladmin: connect to server at 'localhost' failed
error: 'Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)'
Check that mysqld is running and that the socket: '/var/run/mysqld/mysqld.sock' exists!
root@johni-desktop:/usr/bin# locate *.sock
root@johni-desktop:/usr/bin# mysqladmin variables
mysqladmin: connect to server at 'localhost' failed
error: 'Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)'
Check that mysqld is running and that the socket: '/var/run/mysqld/mysqld.sock' exists!
root@johni-desktop:/usr/bin# locate mysqld.sock
root@johni-desktop:/usr/bin# STOPPING server from pid file /var/run/mysqld/mysqld.pid
mysqld_safe[25877]: ended

Can anyone provide insight as to what the problem is and how to resolve it?  
Please keep in mind that I am a newbie; something that may be obvious to you may be totally unknown to me.
Thank you in advance for any assistance you can provide.

---

### Post by adwait on 2006-10-13
I had the same problem....renaming the config file /etc/mysql/my.cnf to something else helped. It says can't start config file but starts the mysql server anyway..no idea how you configure mysql after that though, because if I put the file back in place it gives the same error again...

---

### Post by johnusa on 2006-10-13
I renamed my.cnf and started the server again but received the same "Can't connect to local MySQL ..." error.

Any other suggestion?

---

### Post by uros678 on 2006-10-13
Can you check if the mysql user has read/write permissions on the /var/run/mysqld folder?

Best regards,
Uros

---

### Post by triplep on 2006-10-13
I've seen the upgrading of mySQL cause this, it's mainly due to shifting binary locations and paths.

Have you recently done apt-get update && apt-get upgrade? If you have, your locate DB is out of date most likely(you might want to upgrate to 'slocate' anyhow), run 'updatedb' or, you can learn 'find', which is a pretty useful tool. 

I'd try the following to see if you get multiple results...

find / -name mysql.sock
find / -name mysql

---

### Post by kaiska on 2006-10-13
Same problem here after a dist-upgrade :

```
[ ~ ]-[1]: sudo /etc/init.d/mysql start
Starting MySQL database server: mysqld.
.
.
.
.
.
.
.
.
.
.
.
.
.
...failed or took more than 6s.
        Please take a look at the syslog.
/usr/bin/mysqladmin: connect to server at 'localhost' failed
error: 'Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)'
Check that mysqld is running and that the socket: '/var/run/mysqld/mysqld.sock' exists!
```

mysql user has read/write permissions on /var/run/mysqld folder and I can't find mysqld.sock on the machine.

---

### Post by Smuve on 2006-10-13
I'm not sure exactly what your problem is, but when I was setting up Rails a couple weeks ago, I had a problem with the exact same file.

In Rails, I had to add a line to the "database.yml" configuration file after adapter: mysql,
socket: /var/run/mysqld/mysqld.sock

This told rails where to look for the mysql socket.

After going through this, I would deduct that you may need to update an apache configuration file to tell it where to find mysql at
socket: /var/run/mysqld/mysqld.sock

Hope that helps.

---

### Post by uros678 on 2006-10-13
It is kind of hard to troubleshoot a problem not sitting behind the affected computer. :-k 

A quick check list:

1. check your my.cnf config files if they are okey. All the relevant settings must be righ i.e path to socket files, etc...

2. check for correct permission on the files and dirs in question. Also check for the correct permissions of the folder where the mysql tables reside. Also check who owns the files 

3. Don't manually run mysql, run it with the /etc/init.d script

Sorry I'm not smart enough to solve your problems via the forum. I too had some problems like you guys are experiencing and it all ways was a file permission problem. If my memory serves me correctly that is, it's been a long time ago..:-k 

...and please post the log files relevant to the mysqld error and also my.conf settings.

And perhaps, this is a wild shot, you guys could try to run "touch /var/run/mysqld/mysqld.sock" and chown the file to mysql user and then try to run the mysql daemon.

Best regards,
Uros

---

### Post by Ack99 on 2006-10-16
I had the same problem but my solution was simple.
Simply create the file.
It works!

---

### Post by lazerradial2003 on 2006-10-17
Anyone found a solution to this? If they have could they please talk me through it. Thanks, lazerradial

---

### Post by uros678 on 2006-10-17
First tell us what have you tried allready?

lp,
uros

---

### Post by firemankurt on 2006-10-28
I'm having a very similar problem and have boiled it down to this:

- I add the directory **mysql** to ** /var/run/**
- I set owner to **root** rwx (read,write,execute)
- I set group to **mysql** rwx
- I enter command: **mysqld** as root and mysql runs great.

Problem comes when I restart my computer...
**mysqld** is gone from **/var/run/** and error returns.

I can't figure out why the directory is getting deleted.

---

### Post by angrycat on 2006-11-14
Hello,

I had this error too, in my case it was because I had only installed the mySql client, not the mysql-server](*,) .

It may be worth double checking you havent made the same mistake.

---

### Post by shackleton on 2007-02-03
This problem comes up a number of times. Being a total newby at this, I plowed the internet endlessly and finally made it work. To be honoust I don't really know what fixed it. I followed this guide [https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP), so that will be my point of referrence.

After installation, mysql worked like a charm, after reboot, it failed. Error 2002, etc. Here's what I did:
**Servername**
> Servername 127.0.0.1 in /etc/apache2/apache2.conf, I first entered the IP I get from my router, which was not the same (192.168.1.101) as
> bind-address=127.0.0.1 in /etc/mysql/my.cnf.
I figured it would probably be handy if the two were the same

**Extensions**
The instructions said:
> '$ sudo cp /usr/lib/php5/20051025/mysql.so /usr/lib/php5/ext/mysql.so' I did this for mysql.so AND for mysqli.so at first. Since I don't know what the hell it's for I decided to run the command only for mysql.so.

**Ownage**
I relocated my databasefiles as well but I didn't do that in previous attempts. I don't think it was the problem, but I was thankfull for the post above which told me to do the CHOWN thingy. 

Hopefully this is of any help to anyone.

---

### Post by gerham on 2007-02-23
I had a similar problem.  I had moved an ubuntu vm to a new ip address.  

in the **/etc/mysql/my.cnf** file my *'bind-address'* value was still set to my old ip address.  I set it to 'localhost'  and it worked.  I suspect I could've also set it to the new ip address instead of localhost and it would've worked the same.

-Gerry

---

### Post by pabloles on 2007-03-23
I also had this problem. I changed folder permission /var/run/mysqld to mysql.mysql and chmod it to 755 but it still doesn't work.... I haven't got on my server mysql.sock or mysqld.sock file....

---

### Post by munkiepus on 2007-04-16
Hi you just have to create the socket file 

Create the directory if it is not there:
```
sudo mkdir /var/run/mysqld/
```

touch the file to create it
```
sudo touch /var/run/mysqld/mysqld.sock
```

change the ownership of the folder and socket to the mysql user
```
sudo chown mysql /var/run/mysqld/
```
```
sudo chown mysql /var/run/mysqld/mysqld.sock
```


start the mysql server 
```
sudo mysqld
```

and see if it works

That should do the trick..... well it worked for me :D

---

### Post by johnleonard on 2007-04-25
I had the same problem: overight I suddenly could not connect to  mysql server.

Not being a techy I tried everything I could find in these and other forums but nothing worked. Eventually I decided to reinstall everything to do with mysql using Synaptic. First I backed up my databases in /var/lib/mysql by copying all table binary files (*.frm, *.MYD, and *.MYI files) and their folders elsewhere, then searched for mysql in Synaptic. I then ran a complete uninstall (purge) of mysql-server, mysql-client, etc to remove everything including the configuration files.

Next I reinstalled everything I had just uninstalled through Synaptic,  set the root password and  restarted MySQL using 
$> mysqladmin -u root -p password 
$>mysql -u root -p
It worked!

I then copied all my old database files back into into /var/lib/mysql . I found I had to change ownership and group to mysql before I could access them again:
chown mysql:mysql *

As my server is on localhost I did not need to change my.cnf, but I guess saving a copy of this before purging would have been a good idea too. 

Hope this helps.

---

### Post by prifre on 2007-04-29
I think the reason why I was getting this error was because I only installed the mysql-client and not the mysql-server.

(So you might wanna check that you actually really got the mysql installed before starting it up ;-)

with a smile
/prifre

---

### Post by hotani on 2007-05-17
I just had the same problem, and I think you'll like my fix as it is all GUI. :)

Since I've done this many, many times, it did not make sense that on a fresh ubuntu 6.06 install that suddenly the mysql install would break. So after mucking around with it for a while, I went into synaptic and did a complete removal, then reinstalled. Guess what? MySQL was running fine afterwards. Something is getting gooned up during the installation, and I have no idea what it is, but this should take care of the problem.

---

### Post by Rodrigue on 2007-06-19
I just solved this problem.

Being a n00b at server installation, I avoided touching the my.cnf file.  But somehow it seems that upon installing, mysql hardcoded my machine's ip address in the bind-address parameter.   And since my ip changes sometimes, I had the problem described here. 

Like someone mentioned above, just changing the bind-address to 127.0.0.1 in my.cnf made it work!!  

And to think I was about to reinstall the whole thing!

---

### Post by jedix on 2007-07-17
install portmap

```
apt-get install portmap
```

Cheers,
Liam

---

### Post by gee.rant on 2007-07-27
I have the same problem.
My /etc/mysql/my.cnf file indicates the socket file is at /var/run/mysqld/mysqld.sock
however the mysql client and mysqladmin seem to be using the default /tmp/mysql.sock
To get it to work I used

mysql --socket=/var/run/mysqld/mysqld.sock -u root -p

I'm not sure why the mysql client and mysqladmin are not using the right socket

---

### Post by nomaam on 2007-07-30
I was running MySQL with no problems until I ran apt-get upgrade, now I can't even start MySQL.

I get an error telling me "database list could not be found"

I assume the paths have been changed, but I do not know what I should be changing.

I am using Webmin and the path for my MySQL databases are: /var/lib/mysql   the folder is there but I have no idea what files I should be looking for in there. 

Could someone point me in the right direction in order to get all the paths correct again?

I think its fairly odd for an update to change critical paths... Is this a normal thing to happen when using Ubuntu? If so, would it not be dangerous for a business running Ubuntu to run an update as it could cause many days of down time ???

---

### Post by TrashmanL on 2007-08-07
> I had the same problem but my solution was simple.
Simply create the file.
It works!

It didn't work for me :-( still have the same error.

---

### Post by TrashmanL on 2007-08-09
It's already been mentioned on this forum a few times, but in case they got lost in all the other messages. Creating the file did not work for me, either. I finally got it to work when I made sure I installed ALL of mysql, both client and server. For some reason, the GUI Add/Remove didn't install everything for me, I used 

apt-get install mysql-server-5.0

in a root terminal , it took a little while to install, then it worked fine.

---

### Post by spz on 2007-08-25
I'm using debian and what solved the problem for me was this:
error : ERROR 2002: Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock'.
did a : /etc/init.d/mysql start , mysql fails, and then .. 
syslog: mysqld[25823]: 070825 10:58:16 /usr/sbin/mysqld: unknown variable 'expire_logs_days=10'
so i do: # WARNING: Using expire_logs_days without bin_log crashes the server! See README.Debian!
#expire_logs_days = 10   ... pun an # in front of it and then
/var/log# mysql -u root -p
Enter password:
Reading table information for completion of table and column names
You can turn off this feature to get a quicker startup with -A

Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 6 to server version: 4.0.24_Debian-10sarge2-log

Type 'help;' or '\h' for help. Type '\c' to clear the buffer.

mysql> \q
Bye 

Hope it helps others.

---

### Post by don durito on 2007-08-25
Hi,

i have got the same error after upgrading my apache through the repos.

now mysql won't start. 

I already tried to create the file manualy as it seemed to solve the problem by some of you but still no change.

if anyone of you knows a fix this would be awesome and well rewarded ;-)

---

### Post by Jemy09 on 2007-09-05
Hi,

I had myself the same problem, and no solution of this forum could help me.
At last, I tried something and ... Bing! It worked!

With PHP:
define your HOST not as "localhost" but as "127.0.0.1"
like this: $host = "127.0.0.1";
and connect with:
mysql_connect( $host, $user, $pass );

From the command line:
I had no problem using "mysql -u root -p"
But if this doesn't work, do:
mysql -h 127.0.0.1 -u root -p (or what user you want to log in)

I hope this will help.

Now I am going to look for the "Why this is the solution.." #-o

regards

---

### Post by Jemy09 on 2007-09-07
> **Jemy09 said:**
> Hi,

With PHP:
define your HOST not as "localhost" but as "127.0.0.1"
like this: $host = "127.0.0.1";
and connect with:
mysql_connect( $host, $user, $pass );

regards

Now I found out how to enable PHP connect to MYSQL using "localhost" as hostname.
As mysql is listening on Port: 3306 using Socket: /tmp/mysql.sock, I entered these informations in my "php.ini" and restarted apache.
mysql.default_port = 3306
mysql.default_socket = /tmp/mysql.sock

Now everything runs as I wish! Quite simple...

---

### Post by Ek0nomik on 2007-09-07
> **gerham said:**
> I had a similar problem.  I had moved an ubuntu vm to a new ip address.  

in the **/etc/mysql/my.cnf** file my *'bind-address'* value was still set to my old ip address.  I set it to 'localhost'  and it worked.  I suspect I could've also set it to the new ip address instead of localhost and it would've worked the same.

-Gerry

Thanks, that did the trick.  :)

---

### Post by nazish on 2007-10-21
hi every one .

I had a similar problem after I did a fresh install of ubuntu 7.10 . I figured out a solution, well atleast for my machine. I saw in synaptic that the package mysql-client was installed but the package mysql-server was missing, so I installed it and everything was up and running.

If you have mysql-server already installed try reinstalling it. I think it works in 9/10 cases.

All the best!

---

### Post by posterboy on 2007-10-21
Yes, this is often an issue when running a LAMP stack. I use Amarok a lot, and have it set up such that it uses mysql for it's data. Amarok MUST connect through /var/run/mysqld/mysqld.sock, but no such file exists, because mysql is running in the lamp stack, in the /opt directory. To add further confusion, lamp names this mysql.sock, not mysqld.sock. So, the solution is to create a symlink, like below, that "points" Amarok to the actual connection to mysql. Here:
ls -l
lrwxrwxrwx 1 root root 31 2007-10-20 07:08 mysqld.sock -> /opt/lampp/var/mysql/mysql.sock

HTH

---

### Post by redrack on 2007-10-28
> **posterboy said:**
> Yes, this is often an issue when running a LAMP stack. I use Amarok a lot, and have it set up such that it uses mysql for it's data. Amarok MUST connect through /var/run/mysqld/mysqld.sock, but no such file exists, because mysql is running in the lamp stack, in the /opt directory. To add further confusion, lamp names this mysql.sock, not mysqld.sock. So, the solution is to create a symlink, like below, that "points" Amarok to the actual connection to mysql. Here:
ls -l
lrwxrwxrwx 1 root root 31 2007-10-20 07:08 mysqld.sock -> /opt/lampp/var/mysql/mysql.sock

HTH

got same problem after reboot mysql won't start so i try all this to solve this but it was failed and failed from many times so i think where is the problem , what i did next was to remove /etc/mysql/my.cnf
after i did that i had no problems with mysql and is working verry weel :) sorry for old reply to your post but may help onther users .

---

### Post by resolv_25 on 2007-11-03
I've got the same problem, I can't start mysql, the same error:
```
/usr/bin/mysqladmin: connect to server at 'localhost' failed
error: 'Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)'
Check that mysqld is running and that the socket: '/var/run/mysqld/mysqld.sock' exists!

```
At least, I succeed to save my database, I copied all from */var/lib/mysql/dbname* 
and restore it on another machine, after creating database there.
Then I copied the context from the first pc to another, and finally
```
chown mysql:mysgl *.*
```
The database is ok on another pc.
Still, I can't work on mysql from the first pc..

---

### Post by [mike@theInternet]$ on 2007-12-05
I'm an idiot!  I have been trying to start my freekin mysqld for hours...just realized that my my.cnf bind address had changed!!!!!!!  If you are not static IP, check that first!!!

~Mike

---

### Post by FlashWolf on 2007-12-10
It's simple to solve this question. Just follow these steps:
1 - At terminal, login using 'su' (it's the *root* account. If you still haven't the root password, use: '$ sudo passwd root': type the desired root password and proceed to login to root).
2 - Go to /var directory and type: 'chmod 777 run'.
3 - Start mysqld.
4 - Repeat the step 2, but with the folder /mysqld.
5 - Restart mysqld. It must be running fine. :)1

Keep in mind: Don't worry if the mysqld.sock do not exists. It's kept living while mysqld process is running. So, when you start mysqld again, it'll be created.

---

### Post by cj6814 on 2008-01-25
If your mysql worked fine and then the ip address of your server changed (do to a reboot, restart, power failure, etc) and now you receive the following error when trying to start mysql:

[COLOR="Red"]...failed or took more than 6s.

        Please take a look at the syslog.

/usr/bin/mysqladmin: connect to server at 'localhost' failed

error: 'Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)'

Check that mysqld is running and that the socket: '/var/run/mysqld/mysqld.sock' exists!

user@mybox:~$[/COLOR]

Do the following:

[COLOR="RoyalBlue"]sudo nano /etc/mysql/my.cnf[/COLOR]

scroll down to the "bind-address", you will most likely see the old ip address of your server.  Change the old address to the new ip address of you server.  Save and close (write out) the my.cnf file.

Now start mysql again [COLOR="RoyalBlue"]/etc/init.d/mysql start[/COLOR]

Hopefully, this fixed your problem, it did in my case.

Additional info:

I followed the path to the socket as outlined in the error message ('Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' ).  The mysqld directory was empty which I found very confusing.  However, once you follow the instructions above and successfully restart mysql you will find that the directory then contains the two files that it said you were missing.

---

### Post by gnyanganga on 2008-02-18
I faced a similar problem after upgrading ubuntu.:confused:

Simply created a folder in /var/run named `mysqld` with write access, and bingo!

MySQL start command fired-off as usual...:)

---

### Post by tsnj on 2008-02-18
I had the same problem as someone posted above.  This was a new installation not an upgrade.  Mysql client was installed but the server was not.  I would have thought that this would have been a dependency for phpmyadmin etc.  Didn't have this problem when I installed at home, just here in the office.  It's working fine now.

---

### Post by pichon on 2008-02-25
I tried somthing similar to

> **munkiepus said:**
> Hi you just have to create the socket file 

Create the directory if it is not there:
```
sudo mkdir /var/run/mysqld/
```

touch the file to create it
```
sudo touch /var/run/mysqld/mysqld.sock
```

change the ownership of the folder and socket to the mysql user
```
sudo chown mysql /var/run/mysqld/
```
```
sudo chown mysql /var/run/mysqld/mysqld.sock
```


start the mysql server 
```
sudo mysqld
```

and see if it works

That should do the trick..... well it worked for me :D

And got this:

```

root@pichoWorkshopUbuntu:/var/run/mysqld# touch mysqld.sock
root@pichoWorkshopUbuntu:/var/run/mysqld# chown mysql /var/run/mysqld
root@pichoWorkshopUbuntu:/var/run/mysqld# chown mysql mysqld.sock 
root@pichoWorkshopUbuntu:/var/run/mysqld# ls -l
total 0
-rw-r--r-- 1 mysql root 0 2008-02-25 14:11 mysqld.sock
root@pichoWorkshopUbuntu:/var/run/mysqld# chmod 755 mysqld.sock 
root@pichoWorkshopUbuntu:/var/run/mysqld# ls -l
total 0
-rwxr-xr-x 1 mysql root 0 2008-02-25 14:11 mysqld.sock
root@pichoWorkshopUbuntu:/var/run/mysqld# /etc/init.d/mysql start
 * Starting MySQL database server mysqld
   ...fail!
root@pichoWorkshopUbuntu:/var/run/mysqld# ls -l
total 0
root@pichoWorkshopUbuntu:/var/run/mysqld# 

```

Does anyone know why my file gets deleted?

Thanks
PME

---

### Post by DouglasAWh on 2008-03-03
> **munkiepus said:**
> Hi you just have to create the socket file 

Create the directory if it is not there:
```
sudo mkdir /var/run/mysqld/
```

touch the file to create it
```
sudo touch /var/run/mysqld/mysqld.sock
```

change the ownership of the folder and socket to the mysql user
```
sudo chown mysql /var/run/mysqld/
```
```
sudo chown mysql /var/run/mysqld/mysqld.sock
```


start the mysql server 
```
sudo mysqld
```

and see if it works

That should do the trick..... well it worked for me :D

I'm running from a Mac, but tried this using the path I was given the error for and it did not work.  Any other suggestions?

---

### Post by devinee on 2008-03-14
hi, i'm not very familiar with all this as hubby deals with it but he's in thailand at the mo - sat down last night to watch tv and nothing - tried all solutions i could but to no avail.  i got an email this morning from him to say its due to a full disk and to do the following from a terminal :

ssh mythtv@htpc
sudo rm /var/log/messages
sudo reboot

it worked straight off so hope it helps some of you :)

---

### Post by DouglasAWh on 2008-03-15
> **devinee said:**
> hi, i'm not very familiar with all this as hubby deals with it but he's in thailand at the mo - sat down last night to watch tv and nothing - tried all solutions i could but to no avail.  i got an email this morning from him to say its due to a full disk and to do the following from a terminal :

ssh mythtv@htpc
sudo rm /var/log/messages
sudo reboot

it worked straight off so hope it helps some of you :)

I don't think the MythTV stuff is going to help with MySQL...thanks for trying though.

---

### Post by bmathis on 2008-03-17
> **gee.rant said:**
> I have the same problem.
My /etc/mysql/my.cnf file indicates the socket file is at /var/run/mysqld/mysqld.sock
however the mysql client and mysqladmin seem to be using the default /tmp/mysql.sock
To get it to work I used

mysql --socket=/var/run/mysqld/mysqld.sock -u root -p

I'm not sure why the mysql client and mysqladmin are not using the right socket

This pointed me in the right direction to fix this issue on my server. In my case, I installed Zimbra first (changing Zimbra's web listening port) and then I installed the Lamp stack with this error. I created a link from /var/run/mysqld/mysqld.sock to /tmp/mysqld.sock and then I was able to login and run mysql just fine.
```
sudo ln -s /var/run/mysqld/mysqld.sock /tmp/mysqld.sock
```

---

### Post by DouglasAWh on 2008-03-17
> **devinee said:**
> hi, i'm not very familiar with all this as hubby deals with it but he's in thailand at the mo - sat down last night to watch tv and nothing - tried all solutions i could but to no avail.  i got an email this morning from him to say its due to a full disk and to do the following from a terminal :

ssh mythtv@htpc
sudo rm /var/log/messages
sudo reboot

it worked straight off so hope it helps some of you :)

Hmm, I still don't think clearng the /var/ will fix this problem, but it appears others think MythTV and MySQL problems are related: [http://ubuntuforums.org/showthread.php?t=637458](http://ubuntuforums.org/showthread.php?t=637458)

---

### Post by Aperion on 2008-03-30
I'm really purplexed...
```
chrisnem@chrisnem-dvr:/etc/mysql$ mysqld
The program 'mysqld' is currently not installed.  You can install it by typing:
sudo apt-get install mysql-server-5.0
-bash: mysqld: command not found
chrisnem@chrisnem-dvr:/etc/mysql$ sudo apt-get install mysql-server-5.0
Reading package lists... Done
Building dependency tree
Reading state information... Done
mysql-server-5.0 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.

```

any ideas?

---

### Post by ghostdog2402 on 2008-04-26
> **pichon said:**
> I tried somthing similar to



And got this:

```

root@pichoWorkshopUbuntu:/var/run/mysqld# touch mysqld.sock
root@pichoWorkshopUbuntu:/var/run/mysqld# chown mysql /var/run/mysqld
root@pichoWorkshopUbuntu:/var/run/mysqld# chown mysql mysqld.sock 
root@pichoWorkshopUbuntu:/var/run/mysqld# ls -l
total 0
-rw-r--r-- 1 mysql root 0 2008-02-25 14:11 mysqld.sock
root@pichoWorkshopUbuntu:/var/run/mysqld# chmod 755 mysqld.sock 
root@pichoWorkshopUbuntu:/var/run/mysqld# ls -l
total 0
-rwxr-xr-x 1 mysql root 0 2008-02-25 14:11 mysqld.sock
root@pichoWorkshopUbuntu:/var/run/mysqld# /etc/init.d/mysql start
 * Starting MySQL database server mysqld
   ...fail!
root@pichoWorkshopUbuntu:/var/run/mysqld# ls -l
total 0
root@pichoWorkshopUbuntu:/var/run/mysqld# 

```

Does anyone know why my file gets deleted?

Thanks
PME

It gets deleted becouse the file is there only when youre connected to mysql, so creating  the file wont solve the problem. First you must connect to mysql in terminal:

```
 sudo /etc/init.d/mysql start
```
it should write Ok

then check if the file mysqld.socket is in the directory /var/run/mysqld

finaly you can log in mysql monitor. write in terminal:

```
 mysql -u root -p
```

or in phpmyadmin

hope this helps

---

### Post by sion2k on 2008-05-06
I was having this issue after trying to install Ruby on Rails 2 on Ubuntu 8.04.

After getting the error message of 
```
 Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock'
```

I made sure there wasn't a file where it was looking.
```
ls -la /var/run
```

This concluded there wasn't even a mysqld directory. 

I went ahead and cleaned out as much as I could.
```

sudo apt-get purge mysql-client mysql-client-5.0 mysql-common mysql-server mysql-server-5.0
sudo apt-get autoremove
sudo apt-get autoclean
```

Then updated & installed just what i needed.
```

sudo apt-get update
sudo apt-get upgrade
sudo apt-get install mysql-common mysql-client-5.0 mysql-server-5.0
```

This ran me through the default mysql install were it asks for the mysql admin password, etc. 
I usually leave it blank and then change it anyway, but you could enter whatever you'd like.

After the install was complete I verified mysql was functioning properly.

```

mysql -u root *-p password*
```

If you entered a password use the -p option and specify it. Thats it.
That seemed to work pretty well for me.

---

### Post by joflynn on 2008-05-19
Just had the same error message.  For me the problem was that my /var partition was full.

The solution was just to make space on /var and restart the server.

check disk usage with `df -h`:
                      3.9G  3.9G     0 100% /var

after making space:
                      3.9G  932M  2.8G  25% /var

---

