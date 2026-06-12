---
title: "Medusa help! It returns first word or every word password list as correct!"
date: 2016-12-16
forum: General Help
---

### Post by laztryiii on 2016-12-16
I am new to brute-force hacking and decided to start with medusa. After doing some research  I wanted to try medusa out. So, I decided to try to brute-force my routers username and password using this code.

```
medusa -h 10.0.0.1 -u admin -P /home/user/Desktop/Wordlists/rockyou.txt -M http
``` 

 I took the proper steps to find the correct ports and used Nmap to figure all the information needed out but when I ran the code in my terminal it returned with this saying that 12345 was the right password when I know it is not and won't work if tried. 

```
root@IanHank:/home/user# medusa -h 10.0.0.1 -u admin -P /home/user/Desktop/Wordlists/rockyou.txt -M http -m DOMAIN:127.0.0.1
Medusa v2.2_rc3 [http://www.foofus.net] (C) JoMo-Kun / Foofus Networks <jmk@foofus.net>


ACCOUNT CHECK: [http] Host: 10.0.0.1 (1 of 1, 0 complete) User: admin (1 of 1, 0 complete) Password: 12345 (1 of 14344390 complete)
ACCOUNT FOUND: [http] Host: 10.0.0.1 User: admin Password: 12345 [SUCCESS]

```

There are very few other forums or questions about this and none of their solutions have helped. Maybe because they were posted years ago?Do I need to add a -m (module) to the end. I have a feeling it has something to do with the fact I am testing a local network. Any ideas or answers would be great thanks.

---

### Post by vasa1 on 2016-12-16
> Cracking: Requests for help about any form of password or encryption "cracking" are not supported. Even though there are packages such as aircrack in the repositories, discussions about cracking or software related to cracking often lead to discussions about illegal activities. Such threads will be closed.[From the Forum rules #17]("https://ubuntuforums.org/misc.php?do=showrules")

---

