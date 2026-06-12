---
title: "Problem on installing MySQL"
date: 2007-10-24
forum: General Help
---

### Post by satimis on 2007-10-24
Hi folks,


Ubuntu 7.04 server amd64
MySQL 5.0.38


On installing MySQL and coming to;

$ sudo mysqladmin -h ubuntu.xyz.com root password myrootsqlpassword```

mysqladmin: connect to server at 'ubuntu.satimis.com' failed
error: 'Lost connection to MySQL server at 'reading initial communication packet', system error: 111'

```

$ hostname -f```

ubuntu.xyz.com

```

$ ps aux | grep mysql```

root      4557  0.0  0.0   3860   572 ?        S    20:35   0:00 /bin/sh /usr/bin/mysqld_safe
mysql     4599  0.0  1.0 160556 21992 ?        Sl   20:35   0:00 /usr/sbin/mysqld --basedir=/usr --datadir=/var/lib/mysql --user=mysql --pid-file=/var/run/mysqld/mysqld.pid --skip-external-locking --port=3306 --socket=/var/run/mysqld/mysqld.sock
root      4600  0.0  0.0   3768   576 ?        S    20:35   0:00 logger -p daemon.err -t mysqld_safe -i -t mysqld
satimis   5133  0.0  0.0   5028   828 pts/1    S+   21:15   0:00 grep mysql

```


$ cat /var/log/daemon.log | grep 111
No printout

$ cat /var/log/messages | grep 111```

Oct 23 08:54:28 ubuntu kernel: [   24.857900] ata2.00: ATA-7: Maxtor 6V160E0, VA111900, max UDMA/133
Oct 23 08:54:28 ubuntu kernel: [   33.667111] i2c_adapter i2c-1: nForce2 SMBus adapter at 0x1c40
Oct 23 09:50:31 ubuntu kernel: [   23.021112] io scheduler cfq registered (default)
Oct 23 09:50:31 ubuntu kernel: [   25.185695] ata2.00: ATA-7: Maxtor 6V160E0, VA111900, max UDMA/133
Oct 23 09:50:31 ubuntu kernel: [   27.717111] sd 1:0:0:0: Attached scsi disk sda
Oct 23 09:50:31 ubuntu kernel: [   33.805111] ACPI: PCI Interrupt Link [AAZA] enabled at IRQ 21
Oct 23 19:05:48 ubuntu kernel: [   25.327627] ata2.00: ATA-7: Maxtor 6V160E0, VA111900, max UDMA/133
Oct 23 19:43:21 ubuntu kernel: [   22.142111] ACPI: PCI Interrupt Link [LNK8] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Oct 23 19:43:21 ubuntu kernel: [   25.058170] ata2.00: ATA-7: Maxtor 6V160E0, VA111900, max UDMA/133
Oct 23 19:43:21 ubuntu kernel: [   33.379111] i2c_adapter i2c-0: nForce2 SMBus adapter at 0x1c00
Oct 23 20:35:27 ubuntu kernel: [   24.573772] ata2.00: ATA-7: Maxtor 6V160E0, VA111900, max UDMA/133

```

Please advise which log file I have to check?  How to fix this problem?  TIA


B.R.
satimis

---

### Post by mannih2001 on 2007-10-24
You have the mysql server running on localhost. If you tell the client program to connect to ubuntu.xxx, it will try to connect via an internet socket. Tell it to connect to localhost and you should be fine.

---

### Post by satimis on 2007-10-24
> **mannih2001 said:**
> You have the mysql server running on localhost. If you tell the client program to connect to ubuntu.xxx, it will try to connect via an internet socket. Tell it to connect to localhost and you should be fine.
Could you please advise in more detail.  TIA


B.R.
satimis

---

### Post by mannih2001 on 2007-10-25
Sure.

localhost and ubuntu.satimis.com do not resolve to the same address. The former is your local loop-back device with the IP 127.0.0.1 and the latter (I guess) has a completely different IP address.

MySQL server is listening on localhost for incoming connections, but you tried to connect to ubuntu.satimis.com. You will have to connect to localhost instead:

$ sudo mysqladmin -h localhost root password myrootsqlpassword

---

### Post by satimis on 2007-10-25
> **mannih2001 said:**
> Sure.

localhost and ubuntu.satimis.com do not resolve to the same address. The former is your local loop-back device with the IP 127.0.0.1 and the latter (I guess) has a completely different IP address.

MySQL server is listening on localhost for incoming connections, but you tried to connect to ubuntu.satimis.com. You will have to connect to localhost instead:

$ sudo mysqladmin -h localhost root password myrootsqlpassword
I followed this guide;
The Perfect Setup - Ubuntu Feisty Fawn (Ubuntu 7.04) - Page 4
[http://www.howtoforge.com/perfect_setup_ubuntu704_p4](http://www.howtoforge.com/perfect_setup_ubuntu704_p4)

to proceed.


I have no problem on running;
$ sudo mysqladmin -u root password myrootsqlpassword

password created.


I have problem on running;
sudo mysqladmin -h ubuntu.satimis.com -u root password myrootsqlpassword```

mysqladmin: connect to server at 'ubuntu.satimis.com' failed
error: 'Lost connection to MySQL server at 'reading initial communication packet', system error: 111'

```
Password on both commands are the same.


Using the "myrootsqlpassword" I can run;
$ mysql --user=root --password=myrootsqlpassword```

Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 11
Server version: 5.0.38-Ubuntu_0ubuntu1.1-log Ubuntu 7.04 
distribution

Type 'help;' or '\h' for help. Type '\c' to clear the buffer.

mysql> SHOW mysql LOG FILES;
ERROR 1064 (42000): You have an error in your SQL 
syntax; check the manual that corresponds to your MySQL
server version for the right syntax to use near 'mysql LOG 
FILES' at line 1

```
However it generates another problem on running "SHOW mysql LOG FILES"

Read "man mysql".  The syntax is correct.  I can't figure out how to correct it.  Any advice?  TIA.


According to your advice running;
$ sudo mysqladmin -h localhost root password myrootsqlpassword```

Password:

```
It popup for password.  myrootsqlpassword can't satisfy it.


If typing satimis' password for login on booting the server, it popup;```

mysqladmin: connect to server at 'localhost' failed
error: 'Access denied for user 'root'@'localhost' (using password: NO)'

```

If hitting [Enter]
$ sudo mysqladmin -h ubuntu.satimis.com -u root password myrootsqlpassword
Password: [Enter]
satimis@ubuntu:~$ 

Whether "NO" password created?


satimis

---

### Post by mannih2001 on 2007-10-25
Did you change /etc/mysql/my.cnf and perform a netstat like the howto says? I don't think that the howto is correct; simply commenting out the bind-address setting should not make mysql listen on all interfaces (IMHO the default is localhost). 

Please post the output of the "netstat -tap" command.

Let me add that I don't think that running mysql server on all interfaces is anywhere near "The Perfect Setup". Why would you want to do this?

---

### Post by satimis on 2007-10-25
> **mannih2001 said:**
> Did you change /etc/mysql/my.cnf and perform a netstat like the howto says? I don't think that the howto is correct; simply commenting out the bind-address setting should not make mysql listen on all interfaces (IMHO the default is localhost). 

Yes.

$ sudo netstat -tap | grep mysql```

tcp        0      0 localhost.localdo:mysql *:*                     LISTEN     6313/mysqld         

```
Is it a mistake here "localhost.localdo.mysql"  (I have notes taken down)

localdo ???  Whether should be localdomain ???.  If YES, how to correct the mistake?


> 
Please post the output of the "netstat -tap" command.

Before comment out "bind-address  = 127.0.0.1"

$ sudo netstat -tap```

Password:
Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name   
tcp        0      0 *:vmware-authd          *:*                     LISTEN     4786/xinetd         
tcp        0      0 localhost.localdo:mysql *:*                     LISTEN     4656/mysqld         
tcp        0      0 *:8333                  *:*                     LISTEN     4907/httpd.vmware   
tcp        0      0 *:www                   *:*                     LISTEN     4892/apache2        
tcp        0      0 192.168.0.10:domain     *:*                     LISTEN     4517/named          
tcp        0      0 localhost.locald:domain *:*                     LISTEN     4517/named          
tcp        0      0 192.168.0.10:ssh        *:*                     LISTEN     4751/sshd           
tcp        0      0 localhost.localdoma:ipp *:*                     LISTEN     4573/cupsd          
tcp        0      0 localhost.localdoma:953 *:*                     LISTEN     4517/named          
tcp        0      0 *:8222                  *:*                     LISTEN     4907/httpd.vmware   
tcp6       0      0 *:domain                *:*                     LISTEN     4517/named          
tcp6       0      0 ip6-localhost:953       *:*                     LISTEN     4517/named          

```


$ sudo nano /etc/mysql/my.cnf
comment out "bind-address  = 127.0.0.1"


$ sudo /etc/init.d/mysql restart```

 * Stopping MySQL database server mysqld                                                                    [ OK ] 
 * Starting MySQL database server mysqld                                                                    [ OK ] 
 * Checking for corrupt, not cleanly closed and upgrade needing tables.

```


$ sudo netstat -tap```

Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name   
tcp        0      0 *:vmware-authd          *:*                     LISTEN     4786/xinetd         
tcp        0      0 *:mysql                 *:*                     LISTEN     5295/mysqld         
tcp        0      0 *:8333                  *:*                     LISTEN     4907/httpd.vmware   
tcp        0      0 *:www                   *:*                     LISTEN     4892/apache2        
tcp        0      0 192.168.0.10:domain     *:*                     LISTEN     4517/named          
tcp        0      0 localhost.locald:domain *:*                     LISTEN     4517/named          
tcp        0      0 192.168.0.10:ssh        *:*                     LISTEN     4751/sshd           
tcp        0      0 localhost.localdoma:ipp *:*                     LISTEN     4573/cupsd          
tcp        0      0 localhost.localdoma:953 *:*                     LISTEN     4517/named          
tcp        0      0 *:8222                  *:*                     LISTEN     4907/httpd.vmware   
tcp6       0      0 *:domain                *:*                     LISTEN     4517/named          
tcp6       0      0 ip6-localhost:953       *:*                     LISTEN     4517/named   

```


$ sudo mysqladmin -h ubuntu.satimis.com -u root password myrootsqlpassword```

mysqladmin: connect to server at 'ubuntu.satimis.com' failed
error: 'Lost connection to MySQL server at 'reading initial communication packet', system error: 0'

```
Problem still remains.


> 
Let me add that I don't think that running mysql server on all interfaces is anywhere near "The Perfect Setup". Why would you want to do this?
IIRC, I followed this guide;
[http://onlyubuntu.blogspot.com/2007/05/ubuntu-704-feisty-fawn-lamp-server.html](http://onlyubuntu.blogspot.com/2007/05/ubuntu-704-feisty-fawn-lamp-server.html)

to install Ubuntu 7.04 server amd64 as Host OS on this Virtual machine.  It has been running sometimes without further configured.  Then I spent my time on installing VMWare and Guest OS.

Now I come back to fine-tune it as LAMP server and I found that How-to as my guide.  That is the story.


satimis

---

### Post by mannih2001 on 2007-10-25
OK, so the HOWTO was correct and commenting out Bind-Address made mysql listen on all interfaces.

> Is it a mistake here "localhost.localdo.mysql" (I have notes taken down)

localdo ??? Whether should be localdomain ???. If YES, how to correct the mistake?

That's ok. The netstat command is simply abbreviating its output.

> $ sudo mysqladmin -h ubuntu.satimis.com -u root password myrootsqlpassword

If this fails then maybe ubuntu.satimis.com isn't resolving to your IP address. Can you ping ubuntu.satimis.com?

Please post the output of
host ubuntu.satimis.com

and 
netstat -tan

---

### Post by satimis on 2007-10-25
> 
If this fails then maybe ubuntu.satimis.com isn't resolving to your IP address. Can you ping ubuntu.satimis.com?

Edited /etc/mysql/my.cnf
to uncomment the line "bind-address  = 127.0.0.1"

restarted /etc/init.d/mysql


$ ping -c3 ubuntu.satimis.com```

PING ubuntu.satimis.com (127.0.1.1) 56(84) bytes of data.
64 bytes from ubuntu.satimis.com (127.0.1.1): icmp_seq=1 ttl=64 time=0.069 ms
64 bytes from ubuntu.satimis.com (127.0.1.1): icmp_seq=2 ttl=64 time=0.036 ms
64 bytes from ubuntu.satimis.com (127.0.1.1): icmp_seq=3 ttl=64 time=0.036 ms
--- ubuntu.satimis.com ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2000ms
rtt min/avg/max/mdev = 0.036/0.047/0.069/0.015 ms

```


> 
Please post the output of
host ubuntu.satimis.com

and 
netstat -tan
$ sudo host ubuntu.satimis.com```

Host ubuntu.satimis.com not found: 3(NXDOMAIN)

```


$ sudo netstat -tan```

Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address         State      
tcp        0      0 0.0.0.0:902             0.0.0.0:*               LISTEN     
tcp        0      0 127.0.0.1:3306          0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:8333            0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:80              0.0.0.0:*               LISTEN     
tcp        0      0 172.16.77.1:53          0.0.0.0:*               LISTEN     
tcp        0      0 192.168.213.1:53        0.0.0.0:*               LISTEN     
tcp        0      0 192.168.0.10:53         0.0.0.0:*               LISTEN     
tcp        0      0 127.0.0.1:53            0.0.0.0:*               LISTEN     
tcp        0      0 192.168.0.10:22         0.0.0.0:*               LISTEN     
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN     
tcp        0      0 127.0.0.1:953           0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:8222            0.0.0.0:*               LISTEN     
tcp6       0      0 :::53                   :::*                    LISTEN     
tcp6       0      0 ::1:953                 :::*                    LISTEN     

```

---

### Post by mannih2001 on 2007-10-25
This is a little strange, but the problem you have with mysqladmin now seems to be clear: the host you are trying to talk to simply isn't known.

To finish with your configuration of mysql, I suggest that you simply talk to localhost to set your password and finish the configuration. Thus instead of 

  mysqladmin -h ubuntu.satimis.com -u root password myrootsqlpassword

Simply try 
 
  mysqladmin -h localhost -u root -p myrootsqlpassword

---

### Post by satimis on 2007-10-25
> **mannih2001 said:**
> This is a little strange, but the problem you have with mysqladmin now seems to be clear: the host you are trying to talk to simply isn't known.

To finish with your configuration of mysql, I suggest that you simply talk to localhost to set your password and finish the configuration. Thus instead of 

  mysqladmin -h ubuntu.satimis.com -u root password myrootsqlpassword

Simply try 
 
  mysqladmin -h localhost -u root -p myrootsqlpassword
Very strange

$ sudo mysqladmin -h localhost -u root -p myrootsqlpassword
Password: [Enter]
satimis@ubuntu:~$ 

It asked for password.  On hitting [Enter] it prompted "satimis@ubuntu:~$ ", NO password

---

### Post by satimis on 2007-10-25
Hi mannih2001,


Just having clarified with the author of;
[http://www.howtoforge.com/perfect_setup_ubuntu704_p4](http://www.howtoforge.com/perfect_setup_ubuntu704_p4)

According to;
# netstat -tap | grep mysql```

tcp 0 0 localhost.localdo:mysql *:* LISTEN 6313/mysqld

```


MySQL is listening on 127.0.0.1 only, I don't need following command;```

# mysqladmin -h ubuntu.satimis.com root password myrootsqlpassword

```


Anyway thanks for your assistance.


B.R.
satimis

---

