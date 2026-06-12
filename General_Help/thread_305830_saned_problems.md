---
title: "saned problems"
date: 2006-11-24
forum: General Help
---

### Post by 13ojo on 2006-11-24
Hi,

ive installed sane on a pc.

I can run scanimage on the pc (not screen so causes a lockup when it tries to display).

The scanner seems to be setup and can scan, scanimage crashes but i can see movment of the scanner.

Its scsi btw.

However i can't connect remotely?.

Ive tried using sanetwain. But it gives me a error conencting.


Im wondering wether the default ubuntu install has blocked the port?.

ive put the ips in the files needed. the service is listed in /etc/services

What do you guys think is going on?.

Ps is there a command to scan to a file?. Would be nice as i can acess the files remotely and see if they are scannign properly.

---

### Post by 13ojo on 2006-11-24
seems to be the problem is telnet wont run.

Ive used apt-get install telnetd to install it.

Rebooted.

Nothing.

Its got a /etc/inetd.conf entry 

```
telnet          stream  tcp     nowait  telnetd.telnetd /usr/sbin/tcpd  /usr/sbin/in.telnetd
```

running nmap however gives me jack.


```
Starting Nmap 4.10 ( http://www.insecure.org/nmap/ ) at 2006-11-24 13:07 WST
Interesting ports on localhost (127.0.0.1):
Not shown: 1671 closed ports
PORT     STATE SERVICE
22/tcp   open  ssh
53/tcp   open  domain
80/tcp   open  http
139/tcp  open  netbios-ssn
445/tcp  open  microsoft-ds
901/tcp  open  samba-swat
953/tcp  open  rndc
3306/tcp open  mysql

Nmap finished: 1 IP addres
```

if i try

```
@sudo /usr/sbin/in.telnetd start
```

i get 

```
telnetd: getpeername: Socket operation on non-socket
.
```

but nmap localhost still shows nill.

If i try 

```
telnet localhost 23
```

i get a connection refused error.


I seem to need telnet to be enabled. So these programs work remotely.

Please do not say install SSH, cause i use SSH its installed. But this error seems related to programs using telnet, so it must be installed and running :(


To sum up. How do i make sure telnet is running? it seems not to be

---

