---
title: "Installing bugzilla via apt"
date: 2007-05-28
forum: General Help
---

### Post by f3ua on 2007-05-28
:(:(:(:( GRRR :(:(:(:(

I'm hammering my head on my table because i can't setup bugzilla on my little server.

I've installed apache, perl modules, mysql
Then i did apt-get install bugzilla and setup all via debconf.

```
riccardo@magic-server:~$ sudo dpkg-reconfigure bugzilla
dbconfig-common: writing config to /etc/dbconfig-common/bugzilla.conf

Can't connect to the database.
Error: Access denied for user 'bugzilla'@'localhost' (using password: YES)
  Is your database installed and up and running?
  Do you have the correct username and password selected in localconfig?

```

I can't understand because the user exists on mysql, it seems all ok... where can i get more support on this? I searched the forum with no result.

---

### Post by ^rooker on 2007-06-04
I've also had some permission problems with installing bugzilla using apt-get (although mine were slightly different: no grant permission in database 'bugzilla' for 'debian-sys-maint').


However, for your problem you might want to check the current password for your 'bugzilla' user here:
**/etc/bugzilla/localconfig**. 

Then make sure that the password in there really matches the settings of your database (just copy/paste this user's password).


Good luck!

---

