---
title: "Apache2 doesn't work"
date: 2013-06-01
forum: General Help
---

### Post by Arriva on 2013-06-01
Hello, everybody!
Recently I decided to install local server on my Ubuntu 12.04. And I installed apache2, phpmyadmin, php5 trhough terminal. However, when I'm trying go to "localhost" it shows nothing at all or "localhost/phpmyadmin" it shows error 404, requested url was not found. I reinstalled apache using software center, still nothing works. May be you have any idea what goes wrong?

---

### Post by steeldriver on 2013-06-01
Have you checked that the apache2 service started OK and is listening on the expected port?

```
service apache2 status
```

```
sudo netstat -nlp | grep apache
```

---

### Post by Arriva on 2013-06-01
it says:


```


arriva@arriva-1000H:~$ service apache2 status
Apache2 is running (pid 979).

arriva@arriva-1000H:~$ sudo netstat -nlp | grep apache
tcp6       0      0 :::80                   :::*                    LISTEN      979/apache2
```

---

### Post by JoaoMachado on 2013-06-04
I just recently finished a tutorial on setting up a lamp server on my Ubuntu 13.04 Desktop. It should not be much different than 12.10.
Mu use case was to have multiple sites served from my user directory instead of just /var/www. There may be some helpful hints there that you can use.

[URL="http://joao.machado-family.com/2013/06/04/setup-ubuntu-13-04-local-web-server/"]
http://joao.machado-family.com/2013/06/04/setup-ubuntu-13-04-local-web-server/[/URL]

---

### Post by Arriva on 2013-06-05
Thanks for your notation, but there the guy says that it would work for 13, not for 12. Sorry to say, I cannot aply those knowledge to my system.

---

### Post by steeldriver on 2013-06-05
Well it looks like apache2 is only listening on the tcp6 interface - I'm sorry, I can't really help beyond that as I have no experience with IPv6 however there are a few search hits that might be relevant e.g.

[http://ubuntuforums.org/showthread.php?t=1823846](http://ubuntuforums.org/showthread.php?t=1823846)

[http://serverfault.com/questions/366056/cant-connect-to-tomcat-even-though-its-running](http://serverfault.com/questions/366056/cant-connect-to-tomcat-even-though-its-running)

---

### Post by Arriva on 2013-06-05
Thanks for your suggestion, I'll try to learn about this more. I tried something offered on those forums, the results are:

```
root@arriva-1000H:/home/arriva# netstat -a
Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address         State      
tcp        0      0 *:http                  *:*                     LISTEN     
tcp        0      0 localhost:domain        *:*                     LISTEN     
tcp        0      0 localhost:ipp           *:*                     LISTEN     
tcp        0      0 localhost:mysql         *:*                     LISTEN     
udp        0      0 localhost:domain        *:*                                                  
udp        0      0 localhost:54558         *:*                                


```
These lines about localhost only. I have no idea why when I'm trying to go to localhost it shows just plain blank page, though apache2 is running.

---

### Post by steeldriver on 2013-06-05
what happens if you try with ip6-localhost instead of localhost? or ::1 ?

---

### Post by Arriva on 2013-06-05
If you mean just type in the url of browser, then:

ip6-localhost == still blank page

::1 == address is restricted


also tried 127.0.0.1 == blank page again

---

