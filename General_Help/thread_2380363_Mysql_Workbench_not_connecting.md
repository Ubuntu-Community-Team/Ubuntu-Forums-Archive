---
title: "Mysql Workbench not connecting"
date: 2017-12-16
forum: General Help
---

### Post by tonysar on 2017-12-16
Hello Everyone. 
ubuntu 14.4 on VPS.
Recently moved to vps . after long days and hours, decided to reinstall VPS os from centos to ubuntu. Thus far , decided to only use command lines to setup servers by looking up everything on the net . as far as i know , all services are working. created a vhost and i can access it through domain and display test html page. however, I really need to configure Mysql server. decided to install mysql workbench. i can not seem to connect to remote mysql using workbench. 
i have followed fixes that i could find and yet workbench can not connect to mysqlserver. one of the possible reason was , 127.0.0.1 is bind to the server and fix for many was to comment it out , i did . and nothing work . 
I can access mysql through SSH. and i have **_sequel pro_ **installed and with same connection parameters , i had no issue connecting to remote mysql server. 

so any suggestion as how to work this one out ?
Thanks.

---

### Post by tonysar on 2017-12-16
Ok got this one solved too. 
To use work bench .. i ended up creating new user for mysql using mysql shell with Grant All privilege.
After do that .. make sure you Flush Privilege of mysql database. 
I used SSH over Tcp To connect so just provide your ssh username and pass and for mysql host ,leave at 127.0.0.1 with your new username and pass word that was just created in Mysql . that should do the trick. 
hope this helps others.

---

