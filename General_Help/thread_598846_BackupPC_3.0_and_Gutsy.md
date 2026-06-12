---
title: "BackupPC 3.0 and Gutsy"
date: 2007-10-31
forum: General Help
---

### Post by benblank04 on 2007-10-31
Recently installed Gutsy on a text box with the inventions of installing BackupPC 3.0 and doing some testing for a enterprise environment. Using apt-get install backuppc the installation goes fine, but I cannot access the Web page at all. During the installation I recall getting asked what apache server I want to setup I was presented with 4 different options, "apache, apache-ssl, apache-php and apache2. I believe I picked apache2. Looking for reason's why I get page not found when going to [http://localhost/backuppc](http://localhost/backuppc)
I am a Windows guy warming up to the linux world, thanks in advance!

---

### Post by peachy on 2007-11-09
Is the web browser you are using on the same host you installed backuppc on?

Is apache running? 
```
ps -ef|grep apache
```

---

### Post by wwynn on 2007-11-10
I have the same problem and my answers are yes and yes.

---

### Post by hades_6_6_6 on 2008-01-28
```
sudo chmod 777 /etc/apache2/apache2.conf
sudo cat /etc/backuppc/apache.conf >> /etc/apache2/apache2.conf
sudo chmod 644 /etc/apache2/apache2.conf
sudo /etc/init.d/apache2 stop
sudo /etc/init.d/apache2 start
```

---

