---
title: "Xampp/Lamp + Apache 2"
date: 2016-05-04
forum: General Help
---

### Post by mnduck on 2016-05-04
Lubuntu 16.04

I have Xampp and phpMyAdmin ( inc installing mbstring) up and running but the Lamp stack Apache wont start as Lubuntu has already started Apache 2 what's the best way to resolve this? 


Thanks All.    aamcle

---

### Post by Habitual on 2016-05-04
See [https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

---

### Post by mnduck on 2016-05-04
I've seen that and I've successfully installed LAMP, when I try to start lamp, the FTP and MySQL start but apache cannot as apache2 is already running.

I'm not sure I understand the purpose of that guide, it tells me how to install the stack then how to remove it and then it seems to be telling me how to build the stack manually is this correct? 



Regards                     aamcle

---

### Post by Habitual on 2016-05-05
So, it's already running?
It covers a few topics.
What does "start lamp" mean?
The instructions say how to install it, but "start lamp" is not among those instructions.
There are four components.
```
**L**inux # system is running,.
**A**pache must be running. # sudo service apache2 restart
**m**ysql-server must be running. # sudo service mysql restart
**p**hp5-mysql is enabled.

```
```
sudo apt-get install lamp-server^
``` does it all for you.

You said "apache" and "apache2" in the same breath.

Please run and report the output of
```
sudo dpkg -l | grep apache
```

Thank you.

---

