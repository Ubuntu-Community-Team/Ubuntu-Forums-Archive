---
title: "port 887?"
date: 2005-06-21
forum: General Help
---

### Post by cristianommxp on 2005-06-21
I run nmap with my own computer:

--------------------------------------------------------------------------------------------------------------
$ nmap 172.16.23.22

Starting nmap 3.50 ( [http://www.insecure.org/nmap/](http://www.insecure.org/nmap/) ) at 2005-06-21 09:27 BRT
Interesting ports on 172.16.23.22:
(The 1656 ports scanned but not shown below are in state: closed)
PORT     STATE SERVICE
80/tcp   open  http
887/tcp  open  unknown
5432/tcp open  postgres

Nmap run completed -- 1 IP address (1 host up) scanned in 3.639 seconds
--------------------------------------------------------------------------------------------------------------

But I don't know what's listen in port 887. 

Please, what does port 887 do? Do u know?

10ks


Cristiano M. Magalhaes

---

### Post by intangible on 2005-06-21
Try this: **sudo netstat -ltunp|grep :887**

---

### Post by cristianommxp on 2005-06-22
nothing:


$ sudo netstat -ltunp|grep :887
Password:
$

---

### Post by intangible on 2005-06-22
Are you sure 887 is still open?

Try this:
**sudo netstat -ltunp**

And show me what it says.

---

### Post by cristianommxp on 2005-06-22
$ sudo netstat -ltunp
Conexões Internet Ativas (sem os servidores)
Proto Recv-Q Send-Q Endereço Local          Endereço Remoto         Estado      PID/Program name
tcp        0      0 127.0.0.1:643           0.0.0.0:*               OUÇA       3435/famd
tcp        0      0 127.0.0.1:111           0.0.0.0:*               OUÇA       2865/portmap
tcp        0      0 127.0.0.1:631           0.0.0.0:*               OUÇA       3338/cupsd
tcp        0      0 0.0.0.0:5432            0.0.0.0:*               OUÇA       3618/postmaster
tcp        0      0 127.0.0.1:25            0.0.0.0:*               OUÇA       3567/master
tcp        0      0 0.0.0.0:891             0.0.0.0:*               OUÇA       3677/rpc.statd
tcp6       0      0 :::80                   :::*                    OUÇA       3721/apache2
tcp6       0      0 :::5432                 :::*                    OUÇA       3618/postmaster
tcp6       0      0 ::1:25                  :::*                    OUÇA       3567/master
udp        0      0 127.0.0.1:111           0.0.0.0:*                          2865/portmap
udp        0      0 0.0.0.0:885             0.0.0.0:*                          3677/rpc.statd
udp        0      0 0.0.0.0:888             0.0.0.0:*                          3677/rpc.statd
$


OBS.: "OUÇA" is "LISTEN" in Portuguease

---

### Post by intangible on 2005-06-22
It doesn't seem to be open anymore, does nmap still show it open?

nmap 172.16.23.22    ?

---

### Post by cristianommxp on 2005-06-22
Now I have the port 891 open. I don't understand...

-----------------------------------------------------------------------------
$ nmap 172.16.23.22

Starting nmap 3.50 ( [http://www.insecure.org/nmap/](http://www.insecure.org/nmap/) ) at 2005-06-22 11:15 BRT
Interesting ports on 172.16.23.22:
(The 1656 ports scanned but not shown below are in state: closed)
PORT     STATE SERVICE
80/tcp   open  http
891/tcp  open  unknown
5432/tcp open  postgres

Nmap run completed -- 1 IP address (1 host up) scanned in 0.414 seconds
$
-----------------------------------------------------------------------------

$ sudo netstat -ltunp|grep :891
tcp        0      0 0.0.0.0:891             0.0.0.0:*               OUÇA       3677/rpc.statd

-----------------------------------------------------------------------------


So, whats 891 port?

---

### Post by intangible on 2005-06-22
[http://packages.ubuntu.com/cgi-bin/search_contents.pl?word=rpc.statd&searchmode=searchfiles&case=insensitive&version=hoary&arch=i386](http://packages.ubuntu.com/cgi-bin/search_contents.pl?word=rpc.statd&searchmode=searchfiles&case=insensitive&version=hoary&arch=i386)

Looks like nfs-common.  I don't have that package installed, does anything on your system depend on it?

---

### Post by cristianommxp on 2005-06-22
I have an NFS server, but its disabled

---

### Post by intangible on 2005-06-22
It looks like part of it is still running.

If you do this: **sudo /etc/init.d/nfs-common stop** and then nmap scan yourself, is the port gone?

---

