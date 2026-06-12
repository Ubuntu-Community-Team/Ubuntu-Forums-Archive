---
title: "Rootfs full.... again. [Mysql]"
date: 2013-05-24
forum: General Help
---

### Post by Jeff142 on 2013-05-24
Well i just posted this about 2 weeks a go, about a different server and now it seams my rootfs filled on my mysql server.

The problem is a file called "ibdata1" its huge 18GB. The fix looked eazy on google. but one huge roadblock. 

My rootfs is full and mysql wont start, so how can i dump what i need? looking online i found 

[http://stackoverflow.com/questions/3456159/how-to-shrink-purge-ibdata1-file-in-mysql](http://stackoverflow.com/questions/3456159/how-to-shrink-purge-ibdata1-file-in-mysql)


[LIST=1]
[*]Do a mysqldump of all databases, procedures, triggers etc  (How do i dump when the server is to full to start it?)
[*]Drop all databases **except the mysql database**
[*]Stop mysql
[*]Delete ibdata1 and ib_log files
[*]Start mysql
[*]Restore from dump
[/LIST]
I do not have physical accuses to the box, as its a ovh canada box, any help would be aprecated (anything fancy please put commands)

---

