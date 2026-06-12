---
title: "mysql mess deleting users from mysql.user"
date: 2016-04-13
forum: General Help
---

### Post by tabularassa on 2016-04-13
I have a Dell laptop (Memory 3.8 Processor Intel® Core™2 Duo CPU T6670 @ 2.20GHz × 2 ) running ubuntu 15.10

I was trying to install Lamp, going through this tutorial [http://www.unixmen.com/how-to-install-lamp-stack-on-ubuntu-15-10/](http://www.unixmen.com/how-to-install-lamp-stack-on-ubuntu-15-10/)
I finished the installation quite successfully (or so I thought) and when I tried to enter phpmyadmin none of the user-pass combinations worked for me. I used the same user-pass for each step so I was surprised to find the not working. once or twice I uninstalled mysql  and reinstalled it going through the entire process again each time  
At first I thought there was an issue with the user for mysql so I did  
    mysql> select user,host from mysql.user;
I saw many "root" users and deleted the one that belonged to phpmyadmin and localhost with the intention of setting it back again but I also deleted the one from host "::1"
After doing that not only I wasn't able to continue using phpmyadmin, also anything I wanted to do in mysql led me to a misterious error.
[IMG]https://encrypted-tbn2.gstatic.com/images?q=tbn:ANd9GcQeDoOQH_wmWxtnzKLEVrAf3_5SuNbfoa5XG2fw8h3oTnl0VDsci_WMQ7QQ[/IMG]

I don't know what I did, but I'd like to know if anyone can give me a hint on how to measure the damage and if I should reinstall the whole OS because I broke too many things 


lupe@Brenik:~$ mysql
ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)

/var/run/mysqld/mysqld.sock <-- this file doesn't exist

I know I messed up but I'd like some guidance to see how much damage I made and if there's a possibility of fixing it.

Thanks in advance to all of you!
Cheers!
Lupe

---

### Post by SeijiSensei on 2016-04-14
I'd start by reinstalling mysql-server.

```

sudo apt-get update
sudo apt-get remove --purge mysql-server
sudo apt get install mysql-server

```

You should be prompted to set up a password for the root user during the installation.  If not follow the steps here: [https://www.howtoforge.com/setting-changing-resetting-mysql-root-passwords](https://www.howtoforge.com/setting-changing-resetting-mysql-root-passwords)

---

### Post by tabularassa on 2016-04-15
Hi, [COLOR=#000000]SeijiSensei
Thanks a lot for replying 

Before opening this thread I had already reinstalled everything twice and removed, purged and uninstalled everything once more.
Nontheless, I followed your instructions and It worked.... I don't know what was happening before...but there it is


mysql> SELECT user, host from mysql.user;
+------------------+-----------+
| user             | host      |
+------------------+-----------+
| root             | 127.0.0.1 |
| root             | ::1       |
| root             | brenik    |
| debian-sys-maint | localhost |
| root             | localhost |
+------------------+-----------+
5 rows in set (0,00 sec)


Thank you very much!

[IMG]http://www.autostraddle.com/wp-content/uploads/2013/12/wayne.gif[/IMG]

Now.... looks like I never had a problem but I was  misspelling the command for mysql to give me access
SO now I have everything installed and running but I still don't know what to do about phpmyadmin not recognizing my pass

when I use a non-existent user the login page just stays put, but if I use user 'root' and pass 'root-password' I get this which is at least unexpected
¿any clues on what could be happening there? ¿should I make a new thread on this?

Thanks in advance 

[IMG]http://s23.postimg.org/fnnyk8j7v/Screenshot_from_2016_04_15_19_13_52.png[/IMG]
[/COLOR]

---

