---
title: "lowest permissions for debian_sys_maint"
date: 2014-10-13
forum: General Help
---

### Post by KennethBlok on 2014-10-13
Dear Community,

I am running a server with Ubuntu 14.04 LTS. I have installed MySQL Server 5.6 via apt - using Innodb.
I am aware that MySQL user: debian_sys_maint is responsible for checking several root user, database/table, and log issues at start/stop/restart of MySQL on Ubuntu Server.

I would like to know: To which MINIMAL Database/Table permissions, can I reduce user: debian_sys_maint? 
At install it was bestowed all privileges -which is the equivalent of a MySQL 'root' user. 

Google replies tell me that debian_sys_maint could do with only ROTATE permissions... I'd like to know before experimenting :)

Thank you for you  help in advance.
-K

---

