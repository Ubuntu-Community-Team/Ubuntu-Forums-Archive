---
title: "AvantFax/HylaFax Install"
date: 2014-12-01
forum: General Help
---

### Post by Trevor_Klenke on 2014-12-01
Hello, I'm trying to set up a fax server for my small office and have tried to instal HylaFax with AvantFax. I'm successfully receiving faxes with Hylafax (they are showing up in the received folder) but I'm not able to get AvantFax working correctly. I've installed using the instructions on this post: [http://www.avantfax.com/install.php](http://www.avantfax.com/install.php). The apache 2 page comes up when I type in the address for the server but I haven't been able to get the AvantFax page to come up by typing in [http://xxx.xxx.xxx.xxx/avantfax/admin](http://xxx.xxx.xxx.xxx/avantfax/admin). Any suggestions? I also wasn't able to do the following:

# mysql -uroot -p < create_user.sql
# mysql -uavantfax -pd58fe49 avantfax < create_tables.sql
Mysql is installed on the machine - I installed LAMP prior to installing the modem and HylaFax.

Any suggestions are appreciated!

---

### Post by gordintoronto on 2014-12-02
Are you trying to run two fax programs at the same time? Probably won't work.

What response did you get from the mysql commands? You said they didn't work.

What was the actual ip address you used? I suspect it should have been 127.0.0.1

What exact OS are you running? Are the installation instructions specific to that OS? (The Apache setup is different, even among Canonical OSes.)

---

