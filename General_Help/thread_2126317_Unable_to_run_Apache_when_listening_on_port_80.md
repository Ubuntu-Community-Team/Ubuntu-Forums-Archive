---
title: "Unable to run Apache when listening on port 80"
date: 2013-03-16
forum: General Help
---

### Post by GerritR on 2013-03-16
Although this appears to be an Apache problem,
I believe the cause is in Ubuntu.

Issue ;- When I configure Apache to isten to port 80, it will not start.

It works fine on port 8080.

I believe sometingh else is on port 80.

Did this;-
```
lsof -i :80  
COMMAND    PID USER   FD   TYPE DEVICE SIZE/OFF NODE NAME
ubuntu-ge 1778 hans    7u  IPv4  11099      0t0  TCP hans-GA-78LMT-S2P.local:58177->mistletoe.canonical.com:http (CLOSE_WAIT)
```

What is this and do I need it?

If not, how do I get rid of it?

Please be specific as I am very new to Linux and don't know very much yet.

Am running  12,04 LTS and Lampstack 5.4.10-0
 which includes Apache 2.4

Any help would be appreciated.

Thanks

---

### Post by Doug S on 2013-03-16
Hi and welcome to Ubuntu forums.

I'm not sure, but I think your listing from "lsof -i :80" is showing an outgoing connection from your computer port 58177 to a web page on some canonical server port 80. The connection is just in the prosses of closing. Using your method, and also haveing just fetched a page on from my web server via some client, I get:```
doug@doug-64:~$ [COLOR=#ff0000]sudo lsof -i :80[/COLOR]
COMMAND   PID     USER   FD   TYPE DEVICE SIZE/OFF NODE NAME
apache2  1476     root    3u  IPv4   9740      0t0  TCP *:http (LISTEN)
apache2 20763 www-data    3u  IPv4   9740      0t0  TCP *:http (LISTEN)
apache2 26343 www-data    3u  IPv4   9740      0t0  TCP *:http (LISTEN)
apache2 26344 www-data    3u  IPv4   9740      0t0  TCP *:http (LISTEN)
apache2 26978 www-data    3u  IPv4   9740      0t0  TCP *:http (LISTEN)
apache2 27502 www-data    3u  IPv4   9740      0t0  TCP *:http (LISTEN)
apache2 27503 www-data    3u  IPv4   9740      0t0  TCP *:http (LISTEN)
apache2 28112 www-data    3u  IPv4   9740      0t0  TCP *:http (LISTEN)
apache2 28112 www-data    9u  IPv4 365704      0t0  TCP ns1.smythies.com:http->doug-xps2.smythies.com:6885 (ESTABLISHED)
apache2 28721 www-data    3u  IPv4   9740      0t0  TCP *:http (LISTEN)
apache2 28890 www-data    3u  IPv4   9740      0t0  TCP *:http (LISTEN)
apache2 28948 www-data    3u  IPv4   9740      0t0  TCP *:http (LISTEN)

```Now, this is an example of the method I have seen recommended many times on these forums to see who is listening for TCP connections on what port:```
doug@s15:~$ [COLOR=#ff0000]sudo netstat -plnt[/COLOR]
[sudo] password for doug:
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 192.168.122.1:53        0.0.0.0:*               LISTEN      1900/dnsmasq
tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN      1154/sshd
tcp        0      0 0.0.0.0:25              0.0.0.0:*               LISTEN      1971/master
tcp        0      0 0.0.0.0:443             0.0.0.0:*               LISTEN      2056/apache2
tcp        0      0 0.0.0.0:445             0.0.0.0:*               LISTEN      874/smbd
tcp        0      0 127.0.0.1:3306          0.0.0.0:*               LISTEN      1676/mysqld
tcp        0      0 0.0.0.0:139             0.0.0.0:*               LISTEN      874/smbd
[COLOR=#ff0000]tcp        0      0 0.0.0.0:80              0.0.0.0:*               LISTEN      2056/apache2[/COLOR]

```

---

### Post by matt_symes on 2013-03-17
Hi

A geoip server ? You're running Ubuntu with Unity desktop ?

From the terminal, what does this return ?

```
gsettings list-recursively | grep geoip
```

What about this ?
```
gsettings list-recursively | grep 'mistletoe.canonical.com'
```

Try with and without quotes around mistletoe....

Kind regards

---

### Post by rnerwein on 2013-03-17
> **GerritR said:**
> Although this appears to be an Apache problem,
I believe the cause is in Ubuntu.

Issue ;- When I configure Apache to isten to port 80, it will not start.

It works fine on port 8080.

I believe sometingh else is on port 80.

Did this;-
```
lsof -i :80  
COMMAND    PID USER   FD   TYPE DEVICE SIZE/OFF NODE NAME
ubuntu-ge 1778 hans    7u  IPv4  11099      0t0  TCP hans-GA-78LMT-S2P.local:58177->mistletoe.canonical.com:http (CLOSE_WAIT)
```

What is this and do I need it?

If not, how do I get rid of it?

Please be specific as I am very new to Linux and don't know very much yet.

Am running  12,04 LTS and Lampstack 5.4.10-0
 which includes Apache 2.4

Any help would be appreciated.

Thanks
hi
i belive it too: --> I believe the cause is in Ubuntu.
got the same problem years ago. the reason is a faulty TCP implementations, and leave the server hanging in FIN_WAIT. that means that mistletoe.canonical.com will have
bigger problems - a lot of connections will hang in FIN_WAIT ?!
and surprise on my box --> ubuntu-ge 3075 richi    7u  IPv4 158684      0t0  TCP tschangwifi:37467->mistletoe.canonical.com:http (CLOSE_WAIT)
same behavior. the connection is a three way handshake and i guess an ACK is lost 
ciao

---

### Post by rnerwein on 2013-03-17
> **GerritR said:**
> Although this appears to be an Apache problem,
I believe the cause is in Ubuntu.

Issue ;- When I configure Apache to isten to port 80, it will not start.

It works fine on port 8080.

I believe sometingh else is on port 80.

Did this;-
```
lsof -i :80  
COMMAND    PID USER   FD   TYPE DEVICE SIZE/OFF NODE NAME
ubuntu-ge 1778 hans    7u  IPv4  11099      0t0  TCP hans-GA-78LMT-S2P.local:58177->mistletoe.canonical.com:http (CLOSE_WAIT)
```

What is this and do I need it?

If not, how do I get rid of it?

Please be specific as I am very new to Linux and don't know very much yet.

Am running  12,04 LTS and Lampstack 5.4.10-0
 which includes Apache 2.4

Any help would be appreciated.

Thanks
hi
i belive it too: --> I believe the cause is in Ubuntu.
got the same problem years ago. the reason is a faulty TCP implementations, and leave the server hanging in FIN_WAIT. that means that mistletoe.canonical.com will have
bigger problems - a lot of connections will hang in FIN_WAIT ?!
and surprise on my box --> ubuntu-ge 3075 richi    7u  IPv4 158684      0t0  TCP tschangwifi:37467->mistletoe.canonical.com:http (CLOSE_WAIT)
same behavior. the connection is a three way handshake and i guess an ACK is lost 
ciao
oh - my apache isn't involed in that problem.

---

### Post by GerritR on 2013-03-17
Hi All,

Thanks for the help.

Matt_Symes, 

I tried both your suggestions, got no output at all, just the prompt.

Doug S ;

Did a Netstat and got this 

[FONT=courier new]hans@hans-GA-78LMT-S2P:~$ sudo netstat -plnt
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 127.0.0.1:9000          0.0.0.0:*               LISTEN      1047/php-fpm.conf)
tcp        0      0 0.0.0.0:3306            0.0.0.0:*               LISTEN      9789/mysqld.bin 
tcp        0      0 0.0.0.0:139             0.0.0.0:*               LISTEN      795/smbd        
tcp        0      0 0.0.0.0:8080            0.0.0.0:*               LISTEN      3719/httpd      
tcp        0      0 127.0.0.1:53            0.0.0.0:*               LISTEN      1011/dnsmasq    
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN      803/cupsd       
tcp        0      0 0.0.0.0:8443            0.0.0.0:*               LISTEN      3719/httpd      
tcp        0      0 0.0.0.0:445             0.0.0.0:*               LISTEN      795/smbd        
tcp6       0      0 :::21                   :::*                    LISTEN      1095/proftpd: (acce
tcp6       0      0 ::1:631                 :::*                    LISTEN      803/cupsd       
hans@hans-GA-78LMT-S2P:~$ ^C
hans@hans-GA-78LMT-S2P:~$ [/FONT]


Notice, NO Port 80

How strange that ?

Just tried once again to start Apache on port 80, No luck.

This has got me stumped HELP !!  :confused:

Thanks

---

### Post by matt_symes on 2013-03-17
Hi

Try

```
sudo kill 1778
```

to kill the process and restart apache.

if that does not work try

```
sudo kill -9 1778
```

If you kill it does it respawn ?

EDIT: Extra info

```
matthew-S206:/home/matthew % apt-cache search ubuntu-ge 
geoclue-ubuntu-geoip - Provide positioning for GeoClue via Ubuntu GeoIP services
matthew-S206:/home/matthew %
```

It may be GeoClue.

Does this return anything ?

```
dpkg -l | grep ubuntu-ge
```

You could uninstall it or disable it.

Kind regards

---

### Post by Doug S on 2013-03-17
I am having trouble to understand the geo connection to the main problem. Myself, I believe it to be a red-haring (i.e. an unrelated, yet intersting, issue). However, I'll defer to Matt on this part of it.

So, I see the issue as apache is not running and listening on port 80, so why not? Do you see anything in the log files either in /var/log or /var/log/apache2 that might help? If you try to start apache manually does any error get listed as to why it does not start up? Example:```
doug@s15:~$ [COLOR=#ff0000]sudo service apache2 stop   <<< Just to have it not running.[/COLOR]
 * Stopping web server apache2
 ... waiting    [ OK ]
doug@s15:~$ [COLOR=#ff0000]sudo netstat -plnt   <<< Just to check[/COLOR]
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 192.168.122.1:53        0.0.0.0:*               LISTEN      1900/dnsmasq
tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN      1154/sshd
tcp        0      0 0.0.0.0:25              0.0.0.0:*               LISTEN      1971/master
tcp        0      0 0.0.0.0:445             0.0.0.0:*               LISTEN      874/smbd
tcp        0      0 127.0.0.1:3306          0.0.0.0:*               LISTEN      1676/mysqld
tcp        0      0 0.0.0.0:139             0.0.0.0:*               LISTEN      874/smbd
doug@s15:~$ su[COLOR=#ff0000]do service apache2 start    <<< What do you get for this?[/COLOR]
 * Starting web server apache2
  [ OK ]
doug@s15:~$ su[COLOR=#ff0000]do netstat -plnt    <<< I can not get the "su" to be red, weird.
[/COLOR]Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 192.168.122.1:53        0.0.0.0:*               LISTEN      1900/dnsmasq
tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN      1154/sshd
tcp        0      0 0.0.0.0:25              0.0.0.0:*               LISTEN      1971/master
tcp        0      0 0.0.0.0:443             0.0.0.0:*               LISTEN      13070/apache2
tcp        0      0 0.0.0.0:445             0.0.0.0:*               LISTEN      874/smbd
tcp        0      0 127.0.0.1:3306          0.0.0.0:*               LISTEN      1676/mysqld
tcp        0      0 0.0.0.0:139             0.0.0.0:*               LISTEN      874/smbd
[COLOR=#ff0000]tcp        0      0 0.0.0.0:80              0.0.0.0:*               LISTEN      13070/apache2[/COLOR]
```

---

### Post by matt_symes on 2013-03-17
Hi

> I am having trouble to understand the geo connection to the main  problem. Myself, I believe it to be a red-haring (i.e. an unrelated, yet  intersting, issue). However, I'll defer to Matt on this part of it.

No need to defer to me :)

I was following the idea that some process was listening on port 80 and so apache could not bind to it, especially as  it could bind on port 8080.

However, i was surprised to see that netstat did not show anything bound to port 80.

I am following just on train of thought but, we can, and should follow every path we can think of. After all, we all trying to help the OP.

I may well be, and often am, wrong :D

Kind regards

---

### Post by GerritR on 2013-03-17
Hi All,
 

 Here is some more information to chew on:-
 

 This is the output from the BitNami LampStack -5.4.10-0 GUI log.
 The result of trying to start Apache.  
 

 In Config File :  httpd.conf :-
 

 [FONT=Courier 10 Pitch][FONT=Liberation Serif, serif]With-  [/FONT] Listen :80[/FONT]
 Result:-
 [FONT=Courier 10 Pitch]Starting Apache Web Server...[/FONT]
 [FONT=Courier 10 Pitch]Exit code: 3[/FONT]
 [FONT=Courier 10 Pitch]Stdout:[/FONT]
 [FONT=Courier 10 Pitch]/home/hans/lampstack-5.4.10-0/apache2/scripts/ctl.sh : httpd could not be started[/FONT]
 [FONT=Courier 10 Pitch]Stderr:[/FONT]
 [FONT=Courier 10 Pitch]Syntax OK[/FONT]
 [FONT=Courier 10 Pitch](13)Permission denied: AH00072: make_sock: could not bind to address 0.0.0.0:80[/FONT]
 [FONT=Courier 10 Pitch]no listening sockets available, shutting down[/FONT]
 [FONT=Courier 10 Pitch]AH00015: Unable to open logs[/FONT]
 

 [FONT=Courier 10 Pitch][FONT=Liberation Serif, serif]With- [/FONT] # Listen :80[/FONT]
 [FONT=Liberation Serif, serif]Result :-[/FONT]
 [FONT=Courier 10 Pitch]Starting Apache Web Server...[/FONT]
 [FONT=Courier 10 Pitch]/home/hans/lampstack-5.4.10-0/apache2/scripts/ctl.sh : httpd started at port 808[/FONT]0
 

 So it works with Listen :80 commented out.
 

 This is the Netstat from root with Apache running : ( NOTE : XXX is masking MY Local IP  but is OK)
 

 root@hans-GA-78LMT-S2P:~# netstat -tan  
 Active Internet connections (servers and established)  
 Proto Recv-Q Send-Q Local Address           Foreign Address         State       
 tcp        0      0 127.0.0.1:9000         		 0.0.0.0:*               LISTEN      

 tcp        0      0 0.0.0.0:3306            		 0.0.0.0:*               LISTEN      
 tcp        0      0 0.0.0.0:139           		 0.0.0.0:*               LISTEN      
 tcp        0      0 0.0.0.0:8080           		 0.0.0.0:*               LISTEN      
 tcp        0      0 127.0.0.1:53            		0.0.0.0:*               LISTEN      
 tcp        0      0 127.0.0.1:631          		 0.0.0.0:*               LISTEN      
 tcp        0      0 0.0.0.0:8443           		 0.0.0.0:*               LISTEN      
 tcp        0      0 0.0.0.0:445            		 0.0.0.0:*               LISTEN      
 tcp        1      .XXX:52886		    	 91.189.89.144:80        CLOSE_WAIT  
 tcp6       0      0 :::139                  		:::*                    LISTEN      
 tcp6       0      0 :::21                   		:::*                    LISTEN      
 tcp6       0      0 ::1:631                		 :::*                    LISTEN      
 tcp6       0      0 :::445                 		 :::*                    LISTEN      
 

 without Apache running;-
 root@hans-GA-78LMT-S2P:~# netstat -tan  
 Active Internet connections (servers and established)  
 Proto Recv-Q Send-Q Local Address           Foreign Address         State       
 tcp        0      0 127.0.0.1:9000          		0.0.0.0:*               LISTEN      
 tcp        0      0 0.0.0.0:3306            		0.0.0.0:*               LISTEN      
 tcp        0      0 0.0.0.0:139             		0.0.0.0:*               LISTEN      
 tcp        0      0 127.0.0.1:53            		0.0.0.0:*               LISTEN      
 tcp        0      0 127.0.0.1:631           		0.0.0.0:*               LISTEN      
 tcp        0      0 0.0.0.0:445             		0.0.0.0:*               LISTEN      
 tcp        1      0  XXX52886     	91.189.89.144:80        CLOSE_WAIT  
 tcp6       0      0 :::139                  		:::*                    LISTEN      
 tcp6       0      0 :::21                   		:::*                    LISTEN      
 tcp6       0      0 ::1:631                 		:::*                    LISTEN      
 tcp6       0      0 :::445                  		:::*                    LISTEN   
 

 

 So the only port no open is 8080 when Apache is not running. But it still does not show port 80.
 

 I checked for a firewall but it is inactive and it should not be an ISP block as both PCs are on the same network. I cant even connect to port 80 from the server machine with Firefox, but can on port 8080.
 

 This is all very strange. Can anyone at Ubuntu clarrify this situation Please ??
 

 

 Thanks Much

---

### Post by Doug S on 2013-03-17
I am not familiar with BitNami, but from what I have read in the last few minutes it seems it might typically be installed by normal users and not administrators or root or superusers or whatever you want to call it. Thus you wouldn't have access to lower numbered port (below 1024, I think). Perhaps that is why it defaults to port 8080.
My suggestion is that you search around on the [BiNami forum ]("http://answers.bitnami.org/")for further insight. (I am not saying we won't continue to try to help on this thread.)

---

### Post by GerritR on 2013-03-17
Hi all,
 

 I think I found the problem  From: [http://httpd.apache.org/docs/2.4/invoking.html](http://httpd.apache.org/docs/2.4/invoking.html)
 :-
 If the [Listen]("http://httpd.apache.org/docs/2.4/mod/mpm_common.html#listen") specified in the configuration file is default of 80 (or any other port below 1024), then it is necessary to have root privileges in order to start apache, so that it can bind to this privileged port. Once the server has started and performed a few preliminary activities such as opening its log files, it will launch several *child* processes which do the work of listening for and answering requests from clients. The main httpd process continues to run as the root user, but the child processes run as a less privileged user. This is controlled by the selected [Multi-Processing Module]("http://httpd.apache.org/docs/2.4/mpm.html").
 

 There is more.--- on that page.
 

 Now I only have to figure out the TechSpeak on how to fix it.
 

 GerritR

---

### Post by Doug S on 2013-03-17
Could it be as easy as running the startup script under "sudo"? I.E. instead of this (from the [BitNami quick start quide]("http://wiki.bitnami.org/Infrastructure_Stacks/BitNami_AMP_Stacks#How_do_I_start_and_stop_the_servers.3f")):```
$ cd ~/*applicaton-version*
$ ./ctlscript.sh start

```do this:```
$ cd ~/*applicaton-version*
$ sudo ./ctlscript.sh start

```By the way, have a look at my post #2 above, it shows the root apache task running and also the child non-root tasks.

Also note (for other readers): how to start apache for this BitNami stuff seems to be different than for a "normal" Lamp stack, and thus my post #8 isn't correct for this specific case.

---

