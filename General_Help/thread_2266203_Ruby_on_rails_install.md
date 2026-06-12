---
title: "Ruby on rails install"
date: 2015-02-20
forum: General Help
---

### Post by Extremeshannon on 2015-02-20
Hello everyone. I have unstalled Ruby on rails and I am having a permision problem with MySQL. Can som eone direct me to the config/Database.yml file file. I am not able to find where my rails folder is or this file to edit.

Thanks 
Shannon

---

### Post by TheFu on 2015-02-21
Are you using rvm or rbenv?  Using the system ruby is NOT a best practice for any rails deployment.

Ruby on Rails depends on the cwd for everything. There is a standard layout for every project, based on the version of Rails installed.  The top level directory can be anywhere, but from that location down, it is standard.

MySQL has its own authentication system, so you'll need to know the "root" password for the mysql rdbms to add additional userids - these are generally NOT connected to any login userids on a Linux system.

You can use 'find' or 'locate' to find or locate any file on your system. These are case sensitive names, so doing a case insensitive search would be smart.  In my RoR projects, it is named "database.yml" - so **locate database.yml** finds the many copies of the file. Just install **locate** on the system, run **sudo updatedb**, then run the locate command. You can read up about the difference between locate and find.
The fine command is:
**find / -iname database.yml -type f -print**
if you don't know where the file is.  It can be very slow.

---

