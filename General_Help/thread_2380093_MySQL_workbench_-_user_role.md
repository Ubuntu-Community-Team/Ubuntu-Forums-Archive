---
title: "MySQL workbench - user role"
date: 2017-12-13
forum: General Help
---

### Post by ELMIT on 2017-12-13
I am new to workbench. 

I want to create a user and assign him one database.
User:  dog
database: dog
password: doglover


I started in workbench to add a "New a schema in the connected"

At the Login tab:
I added Login Name: dog
Authentication Type: Standard
Limit to Hosts Matching: localhost
Password: doglover
Confirm Password: doglover

At the tab Account Limits I don't change anything

At Administrative Roles I doubt which role I should choose. DBA would mean ALL databases, which I definitely not want to give to a user.
The closest what I could think of is DBManager, but it bothers me, that it says "grants full rights on **_all_** databases"
DBManager includes the roles DBDesigner and BackupAdmin. - seems also fine.

---

