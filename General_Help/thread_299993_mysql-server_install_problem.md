---
title: "mysql-server install problem"
date: 2006-11-15
forum: General Help
---

### Post by dsb on 2006-11-15
I am having trouble installing mysql-server. Here is the output:

```

01. Setting up mysql-server-5.0 (5.0.24a-9) ...
02.  * Stopping MySQL database server mysqld                                                                        [ ok ] 
03.  * Starting MySQL database server mysqld                                                                        [fail] 
04. invoke-rc.d: initscript mysql, action "start" failed.
05. dpkg: error processing mysql-server-5.0 (--configure):
06.  subprocess post-installation script returned error exit status 1
07. dpkg: dependency problems prevent configuration of mysql-server:
08.  mysql-server depends on mysql-server-5.0; however:
09.   Package mysql-server-5.0 is not configured yet.
10. dpkg: error processing mysql-server (--configure):
11.  dependency problems - leaving unconfigured
12. Errors were encountered while processing:
13.  mysql-server-5.0
14.  mysql-server
15. E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Additionally, I have tried 
```
sudo apt-get install -f
```
which results to the same error. It was suggested that I try:
```
sudo dpkg install -f
```
but that command returned:
```
dpkg: need an action option

```

I have also tried similar install methods on a different machine, but have received the same error response. Is there something that I am doing wrong?

---

### Post by koenn on 2006-11-15
As it says in the error msg
> 
05. dpkg: error processing mysql-server-5.0 (--configure):
06.  subprocess post-installation script returned error exit status 1
07. dpkg: dependency problems prevent configuration of mysql-server:
08.  mysql-server depends on mysql-server-5.0; however:


you might try to reconfigure mysql-server-5.0 : 
```
sudo apt-get install mysql-server-5.0
sudo dpkg-reconfigure mysql-server-5.0 
```

then, see if any pending installation tasks need fixing, with
```
sudo apt-get install -f
```

take note of any output, so that, if this doesn't work, you know what to look for.

---

### Post by dsb on 2006-11-15
Hi, thanks for the help, but I still get the same errors after
```
sudo apt-get install mysql-server-5.0
```

So then I try
```
sudo dpkg-reconfigure mysql-server-5.0
```

with the results of
```
/usr/sbin/dpkg-reconfigure: mysql-server-5.0 is broken or not fully installed

```

And then the last code
```
sudo apt-get install -f
```
returns the same original error messages.

---

### Post by sfunk1x on 2006-11-15
Yep, I'm having very similar issues. I'm about ready to just trash the install and reinstall fresh with 6.10. I was from 5.10 to 6.06, up to 6.10 now, and it killed the mysql serve ron my box which serves stats for a game server. Really sucks, but I don't have time to jump through a ton of hoops.

Well, I suppose.. it's either a reinstall and I jump through hoops to reconfigure everything, or I jump through hoops to reinstall mysql and use the database I already have.

---

### Post by zquid on 2007-03-02
me to, exact same problem, exact same error messages...

---

### Post by Solyomszem on 2007-03-03
Hi guyz!

 I also have the same problem... (Somewhere I read that You should try to uncomment the following line from /etc/mysql/my.cnf

ski-innodb
)

 It did not work for me...
So if anybody comes up with an acceptable solution... :)

---

### Post by Solyomszem on 2007-03-03
Ok, maybe I have some solution for the problem...

 "Fixed my problem.
I had recently changed from wifi to ethernet so my internal ip was changed.
/etc/mysql/my.cnf
had an entry to bind my old ip-adress. After I changed that entry to localhost everything worked out. Maybe you have a similar problem?"

 From this thread: [http://www.ubuntuforums.org/showthread.php?t=339505&highlight=mysql-server-5.0](http://www.ubuntuforums.org/showthread.php?t=339505&highlight=mysql-server-5.0)

 Bye

---

### Post by Laterix on 2007-03-05
I had the very same errors and the reason for me was that I had commented too many lines from /etc/network/interfaces, because of Network Manager applet.

Now I have all, but these lines commented and it works:
```

auto lo
iface lo inet loopback

```

---

### Post by DrRootabega on 2007-06-22
Uncommenting the lines in /etc/network/interfaces worked for me as well.
Thanks

---

