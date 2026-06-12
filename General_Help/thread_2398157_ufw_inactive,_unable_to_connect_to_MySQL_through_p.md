---
title: "ufw inactive, unable to connect to MySQL through port 3337"
date: 2018-08-08
forum: General Help
---

### Post by csw012 on 2018-08-08
Hi,
I'm trying to connect to a MySQL database through port 3337, but it keeps failing. 
I think it is not a MySQL problem because I'm able to connect using port 3306.

This is the command I'm using:
```
mysql --host=ensembldb.ensembl.org --port=3337 --user=anonymous
```

My ufw is inactive and I tried doing: 
```
nc -zv ensembldb.ensembl.org 3306         
Connection to ensembldb.ensembl.org 3306 port [tcp/mysql] succeeded!
```
```

nc -zv ensembldb.ensembl.org 3337
Connection to ensembldb.ensembl.org 3337 port [tcp/*] succeeded!
```

I don't understand what can be the problem, any suggestions?
Thank you

---

### Post by yigal-l on 2018-08-08
What is the output of ```
netstat -natp
``` when you run it with the same user that runs MySQL, in both cases (port 3306 and 3337)?

---

### Post by csw012 on 2018-08-09
This is the output:

```
sara@isabella-desktop:~$ sudo netstat -natp
[sudo] password di sara: 
Connessioni Internet attive (server e stabiliti)
Proto CodaRic CodaInv Indirizzo locale        Indirizzo remoto       Stato       PID/Program name
tcp        0      0 127.0.0.1:3306          0.0.0.0:*               LISTEN      1015/mysqld     
tcp        0      0 127.0.1.1:53            0.0.0.0:*               LISTEN      1104/dnsmasq    
tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN      983/sshd        
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN      3494/cupsd      
tcp        0      0 192.168.11.58:38422     104.16.78.166:443       ESTABLISHED 3775/firefox    
tcp        0      0 192.168.11.58:37152     93.184.220.29:80        ESTABLISHED 3775/firefox    
tcp        0      0 192.168.11.58:60344     143.204.15.62:443       ESTABLISHED 3775/firefox    
tcp        0      0 192.168.11.58:36840     151.101.129.69:443      ESTABLISHED 3775/firefox    
tcp        0      0 192.168.11.58:45186     151.101.64.134:443      ESTABLISHED 3775/firefox    
tcp        0      0 192.168.11.58:42192     216.58.205.142:80       TIME_WAIT   -               
tcp        0      0 192.168.11.58:36696     198.252.206.25:443      ESTABLISHED 3775/firefox    
tcp        0      0 192.168.11.58:52842     216.58.205.133:443      ESTABLISHED 3775/firefox    
tcp        0      0 192.168.11.58:59120     216.58.205.141:443      TIME_WAIT   -               
tcp        0      0 192.168.11.58:38820     216.58.205.131:443      ESTABLISHED 3775/firefox    
tcp        0      0 192.168.11.58:57376     52.39.181.191:443       ESTABLISHED 3775/firefox    
tcp        0      0 192.168.11.58:54122     216.58.198.42:443       TIME_WAIT   -               
tcp        0      0 192.168.11.58:52630     143.204.15.3:443        ESTABLISHED 3775/firefox    
tcp        0      0 192.168.11.58:53892     216.58.205.138:443      ESTABLISHED 3775/firefox    
tcp        0      0 192.168.11.58:47858     23.33.15.129:443        ESTABLISHED 3775/firefox    
tcp        0      0 192.168.11.58:48308     193.206.135.170:80      TIME_WAIT   -               
tcp        0      0 192.168.11.58:53196     193.206.135.154:80      ESTABLISHED 3775/firefox    
tcp        0      0 192.168.11.58:37438     216.58.205.132:443      ESTABLISHED 3775/firefox    
tcp        0      0 192.168.11.58:57384     193.206.135.178:80      ESTABLISHED 3775/firefox    
tcp        0      0 192.168.11.58:39972     216.58.198.1:443        ESTABLISHED 3775/firefox    
tcp        0      0 192.168.11.58:43424     143.204.8.62:443        TIME_WAIT   -               
tcp        0      0 192.168.11.58:37634     216.58.205.142:443      ESTABLISHED 3775/firefox    
tcp        0      0 192.168.11.58:39800     192.0.73.2:443          ESTABLISHED 3775/firefox    
tcp        0      0 192.168.11.58:43530     216.58.198.14:443       ESTABLISHED 3775/firefox    
tcp        0      0 192.168.11.58:39318     64.233.166.189:443      ESTABLISHED 3775/firefox    
tcp        0      0 192.168.11.58:54120     216.58.198.42:443       TIME_WAIT   -               
tcp        0      0 192.168.11.58:51620     151.101.120.134:443     ESTABLISHED 3775/firefox    
tcp        0      0 192.168.11.58:60102     52.11.194.178:443       ESTABLISHED 3775/firefox    
tcp        0      0 192.168.11.58:35714     64.233.184.94:443       ESTABLISHED 3775/firefox    
tcp        0      0 192.168.11.58:40796     31.13.86.38:443         ESTABLISHED 3775/firefox    
tcp        0      0 192.168.11.58:44632     31.13.86.4:443          ESTABLISHED 3775/firefox    
tcp        0      0 192.168.11.58:49160     216.58.198.10:443       ESTABLISHED 3775/firefox    
tcp        0      0 192.168.11.58:42532     172.217.23.78:443       ESTABLISHED 3775/firefox    
tcp        0      0 192.168.11.58:38834     216.58.205.131:443      ESTABLISHED 3775/firefox    
tcp        0      0 192.168.11.58:48020     18.194.57.153:443       TIME_WAIT   -               
tcp        0      0 192.168.11.58:57640     216.58.205.200:443      ESTABLISHED 3775/firefox    
tcp6       0      0 :::22                   :::*                    LISTEN      983/sshd        
tcp6       0      0 ::1:631                 :::*                    LISTEN      3494/cupsd
```

---

### Post by yigal-l on 2018-08-12
This shows MySQL listening on port 3306. What's the output when it's configured to port 3337?

---

### Post by csw012 on 2018-08-27
It turned out to be another firewall (that we didn't know existed) of the University network that was blocking port 3337.
Thank you for your help.

---

