---
title: "mythtv/mysql issues"
date: 2006-08-18
forum: General Help
---

### Post by fusion_05 on 2006-08-18
hey everyone...i'm quite a ubuntu noob, so bear with me. =)  I'm setting up a mythtv box and everythings going just fine, until i do mythfilldatabase.  I get this:


DB Error (Inserting into dd_schedule):
Query was:
INSERT INTO dd_schedule (programid,stationid,scheduletime,duration,repeat,stereo,subtitled,hdtv,closecaptioned,tvrating,partnumber,parttotal,endtime) VALUES('SH4010240000','24634','2006-08-22T22:00:00','04:00:00',0,0,0,0,0,NULL,0,0,'2006-08-23T02:00:00');
Driver error was [2/1064]:
QMYSQL3: Unable to execute query
Database error was:
You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'repeat,stereo,subtitled,hdtv,closecaptioned,tvrating,partnumber,parttotal,endtim' at line 1




What should i do?

---

### Post by mrashley on 2006-08-18
I think that mythdatabasefill wants you to have mysql 4.1, and you've probably got version 5.0 installed. Check that, if that's the case then you might find some success with

```
sudo aptitude install mysql-client-4.1 mysql-server-4.1
```

to install the older version of mysql.

---

