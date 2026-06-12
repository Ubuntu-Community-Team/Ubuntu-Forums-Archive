---
title: "How to run an application as root user"
date: 2013-01-14
forum: General Help
---

### Post by ruwan2 on 2013-01-14
Hi,

I have an application. After installation, it has a short cut icon on the Desktop. Its property shows that it executes:

/opt/ti/ccsv5/eclipse/eclipse 

According to the application new requirement, it should run as root user. I have tried in a terminal (I intend to run it through in a terminal. Then I change the icon command line):

/opt/ti/ccsv5/eclipse/./eclipse 

./opt/ti/ccsv5/eclipse/eclipse 

sudo ./opt/ti/ccsv5/eclipse/eclipse 

sudo /opt/ti/ccsv5/eclipse/./eclipse 

All do not work. Could you tell me a method to run the application easily? Then, I'll not type so many command to run the application.
Thanks

---

### Post by sffvba[e0rt on 2013-01-14
Why all the random dots . in your commands?

Have you tried:

*sudo /opt/ti/ccsv5/eclipse/eclipse *


404

edit: Also, if it is a graphical application better to use **gksudo**

---

### Post by ruwan2 on 2013-01-14
Thanks. I get the message with your suggestion:

[COLOR=Blue]root@ruwn2-MS-7696:/# sudo /opt/ti/ccsv5/eclipse/eclips
sudo: /opt/ti/ccsv5/eclipse/eclips: command not found
[/COLOR]

---

### Post by ruwan2 on 2013-01-14
Hi,

These files attributes are helpful to solve my problem? Thanks,


[COLOR=SeaGreen]-rwxr-xr-x  1 root  root   63001 Aug 10  2010 eclipse*
-rwxr-xr-x  1 root  root     216 Jan 13 11:45 eclipse.ini*
[/COLOR]

---

### Post by zombifier25 on 2013-01-14
> **ruwan2 said:**
> Thanks. I get the message with your suggestion:

[COLOR=Blue]root@ruwn2-MS-7696:/# sudo /opt/ti/ccsv5/eclipse/eclips
sudo: /opt/ti/ccsv5/eclipse/eclips: command not found
[/COLOR]

You forgot an "e" there.
```
/opt/ti/ccsv5/eclipse/eclips**e**
```

---

