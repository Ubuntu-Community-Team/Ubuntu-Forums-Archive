---
title: "automysqlbackup script and mysql users"
date: 2008-05-14
forum: General Help
---

### Post by TehSnarf on 2008-05-14
I'm looking for a safe, easy way to use the automysqlbackup.2.5.sh script on a cron.daily job, but I'm not sure what a safe and easy way to set up a user to access the databases to back up. I don't think it's really safe to put my mysql root/password in a text file, and I'm not really familiar enough with mysql unfortunately. 

So far, I've got one script modified to just dump my mythconverg database, but I'm wanting to create another user that has read only access, but to everything?, in order to grab everything at a different time. Any suggestions?

---

