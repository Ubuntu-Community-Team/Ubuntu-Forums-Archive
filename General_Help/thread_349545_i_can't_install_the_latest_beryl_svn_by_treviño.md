---
title: "i can't install the latest beryl svn by treviño"
date: 2007-01-30
forum: General Help
---

### Post by jfca283 on 2007-01-30
i add the specific lines in my sources list
then when i import the key to activate them, i get a message, saying something about a problem connecting to the repository
so, how can i fix that?
thanks

---

### Post by jfca283 on 2007-01-30
the message with the key
```
juan@juan-desktop:~$ wget http://download.tuxfamily.org/3v1deb/DD800CD9 -O- | sudo apt-key add -
--14:27:11--  http://download.tuxfamily.org/3v1deb/DD800CD9
           => `-'
Resolving download.tuxfamily.org... Password:
88.191.250.18
Connecting to download.tuxfamily.org|88.191.250.18|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
14:27:21 ERROR 404: Not Found.

gpg: no valid OpenPGP data found.
```

the lines that i added in the sources.list
[b]deb [http://3v1n0.tuxfamily.org](http://3v1n0.tuxfamily.org) dapper beryl-svn
deb-src [http://3v1n0.tuxfamily.org](http://3v1n0.tuxfamily.org) dapper beryl-svn[/b]

i don't know what the hell is the problem...

---

### Post by jfca283 on 2007-01-30
i solved it 
it was a mistake with the repos
they were not the corrects

---

